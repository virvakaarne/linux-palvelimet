*h1*

**Raportin kirjoittaminen – tiivistelmä**
-	Tietotekniseen raporttiin tulee selittää yksityiskohtaisen tarkasti testauksen vaiheet, ympäristö, tulokset ja aika.
-	Raportti kirjoitetaan menneessä aikamuodossa ja sen kieliasun pitää olla huoliteltu (oikeinkirjoitus ja kielioppi oikein, tekstin jakaminen kappaleisiin ja väliotsikoihin).
-	Tieteellinen vilppi ja tekijänoikeuksien rikkominen ei ole sallittua. Lähdeviitteet on merkittävä.
-	Työvaiheet kuvataan konkreettisesti ja tarkasti.
-	Myös virheelliset tulokset raportoidaan, pyritään ratkaisemaan ja tarvittaessa ilmoitetaan sopivalle taholle korjaamista varten.
-	Raportti on hyvin toistettavissa: siinä kuvatun työn kulun pitäisi johtaa jokaisella testaajalla samaan lopputulokseen.
  
**Linux-virtuaalikoneen asentaminen**
 	
***Virtualboxin lataus ja asennus***

Latasin Virtualboxin asennusohjelman osoitteesta https://www.virtualbox.org/wiki/Downloads. Etusivulla oli lueteltu usea versio ohjelmasta host-koneen käyttöjärjestelmän perusteella; tein asennuksen omalla tietokoneellani, joka on malliaan Lenovo Ideapad 3 14ADA05 ja käyttöjärjestelmältään Windows 11 Home, joten valitsin Virtualboxin version ”Windows hosts”.
Virtualboxia asentaessa tuli ilmoitus, jonka mukaan Python Core Package ja win32api.bindings tulisi asentaa Python-bindingien toimimiseksi kunnolla. Ohjelma kuitenkin sanoi myös, että nämä voisi asentaa myöhemminkin enkä ollut varma, tultaisiinko näitä kurssilla tarvitsemaan, joten jätin asian toistaiseksi huomiotta.

***Linux Debianin lataus***

Hain Debianin asennuksessa vaadittavan ison hakemalla Googlesta ”Debian live iso” ja päädyin sivulle https://www.debian.org/CD/live/. Tällä sivustolla klikkasin itseni Debian.orgin etusivulle vasemman yläkulman logosta, ja latasin levykuvan klikkaamalla Download-linkkiä. Levykuva debian-13.0.0-amd64-netinst.iso asentui muutamassa minuutissa ja oli valmis klo 20.31. Siirsin iso-tiedoston Lataukset-kansiosta kansioon C:\users\lotta\Documents\Koulutyöt\Haaga-Helia\Linux-palvelimet omaa navigointia helpottaakseni.
***Virtuaalikoneen asennus Virtualboxilla***
Valitsin Virtualboxin ylälaidasta ”Machine”  ”New…” Tästä auenneeseen ikkunaan kirjoitin ensin virtuaalikoneen perustiedot: nimi (Name) ”DebianVirvaKiljunenCom”, valitsin virtuaalikoneen sijainniksi (VM Folder) taas tämän opintojakson kansion C:\Users\lotta\Documents\Koulutyöt\Haaga-Helia\Linux-palvelimet ja valitsin levykuvaksi (ISO Image) aiemmin asentamani Debian-levykuvan. Klikkasin ruksin pois ruudusta ”Proceed With Unattended Installation” ja siirryin seuraavalle välilehdelle.
Asetin RAM-muistin määräksi 4000 MB, prosessoreiden määräksi yksi ja virtuaalisen kovalevyn kooksi 20,00 GB. Ohjelma ei tarjonnut mahdollisuutta dynaamiseen allokointiin; arvelin valinneeni Virtualboxin käytön ”Expert Modessa” liian myöhään, joten peruutin virtuaalikoneen luonnin ja aloitin sen uudelleen alusta aiemmin kuvattuun tapaan. Uudella yrityksellä asennusikkunassa oli enemmän vaihtoehtoja. Valitsin pudotusvalikosta virtuaalikovalevyn tyypiksi ”VDI (Virtual Disk Image)” ja jätin tyhjäksi ruudun ”Pre-allocate Full Size”, koska oletin näin valitsevani dynaamisen allokoinnin. Välilehdeltä ”Set up unattended guest OS installation” en muuttanut mitään.
***Debianin ensikäynnistys***
Käynnistin virtuaalikoneen kaksoisklikkaamalla sitä Virtualboxin Machines-näkymässä. Valitsin ”Graphical Install” ja asetin seuraavat valinnat: kieli suomi, sijainti Suomi, näppäimistö suomalainen. Asetin koneen nimeksi ”vinski”, verkkosijainnin nimeksi ”vinski-linux” sekä määritin vahvan pääkäyttäjän salasanan. Pääkäyttäjän koko nimi ”Virva Kiljunen” ja käyttäjätunnus ”virva”. Lopuksi asetin vielä peruskäyttäjien salasanan.
Levyosioihin valitsin koko levyn käytön ja vain yhden levyosion. Asennuksen edetessä kieltäydyin ylimääräisen asennusmedian asentamisesta.
Pakettienhallintaohjelman asetukset määritin seuraavasti: asennuspalvelimen maa Suomi, Debian-asennuspalvelin deb.debian.org ja jätin http-välipalvelimen kentän tyhjäksi. Debianin pakettimittariin jätin osallistumatta (valinta ”En”). Lopuksi valitsin asennettavaksi vain valmiiksi annetut Debianin perustyökalut eli ”Debian desktop environment”, ”GNOME” ja ”Vakiot järjestelmätyökalut”.
***Kaatuminen kesken asennuksen ja uusi yritys***
Kesken ohjelmien asennuksen virtuaalikone lakkasi toimimasta virheilmoituksen saattamana. Päätin varmuuden vuoksi poistaa virtuaalikoneen kokonaan ja ladata aiemmin käyttämäni levykuvan sijaan tarkalleen sen, joka kurssin ohjeissa oli neuvottu, eli debian-live-13.0.0-amd64-lxde.iso.
Loin virtuaalikoneen muuten samalla tavalla kuin yllä kuvattu, mutta kaksi oleellista asiaa lisäsin: laitoin ruksin kohtaan ”Use EFI”, jota en ollut aiemmin tehnyt. Ennen uuden virtuaalikoneen luomista myös tarkistin koneeni BIOS:sta, oliko virtuaaliteknologian käyttö päällä (koneen sammutus  käynnistyksen yhteydessä F2-näppäin).
Virtuaalikone kaatui jälleen testatessani nettiselaimen toimivuutta: koettaessani siirtyä osoitteeseen www.haaga-helia.fi kone jumiutui, kunnes Virtualbox Oracle antoi virheilmoituksen. Sen sijaan komentokehotteella tehdyt pienet testit (käskyt whoami ja date) toimivat oikein.
Käynnistin koneen uudelleen komentorivin käskyllä ”sudo reboot” ja valitsin aloitusvalikosta ”Start Installation”. Valitsin kieleksi englannin, sijainniksi ”other  Europe  Finland”, näppäimistöksi en-US.UTF-8 ja suomi. Hostname ”linux-test”, domain ”example.com”. Aiemmasta yrityksestä poiketen jätin root passwordin määrittämättä.
Virtuaalikone kaatui kolmannen kerran asennuksen aikana. Tämänkertainen virheilmoitus antoi viestin ”HostMemoryLow”, jonka pohjalta totesin kaatumisten johtuvan todennäköisesti siitä, että virtuaalikone ei pystynyt käyttämään kaikkea tarvitsemaansa RAM-muistia, jos minulla oli muita ohjelmia kuten tekstieditori ja nettiselain päällä. Kokeilin ratkaisuksi vähentää virtuaalikoneen RAM:ia 2048 megatavuun. Tämän jälkeen asennus onnistui loppuun saakka.
 **Lähteet**
Heinonen, J. 2025. How to Install Linux to Virtualbox? https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md, luettu 25.8.2025.
Karvinen, T. 2006. Raportin kirjoittaminen. https://terokarvinen.com/2006/raportin-kirjoittaminen-4/, luettu 25.8.2025.
