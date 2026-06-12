---
title: "Internet explorer installation problems"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by razo559 on 2006-10-30
hello, Im new to this ubuntu and so far its easy, upto the installation part, i've been trying to install ie on ubuntu and this is what i get when i try to install it::

Wine 0.9.9
Wine 0.9.9
Wine 0.9.9
Welcome, razo! I'm IEs4Linux.
I can install IE 6, 5.5 and 5.0 for you easily and quickly.
You are just four 'enter's away from your IEs.

I'll ask you some questions now. Just answer y or n (default answer is the bold one)

IE 6 will be installed automatically.
Do you want to install IE 5.5 SP2 too? [ y / n ]

And do you want to install IE 5.01 SP2? [ y / n ]

IEs can be installed using one of the following locales:
EN-US PT-BR DE FR ES IT NL SV JA KO NO
DA CN TW FI PL HU AR HE CS PT RU EL TR
Default is EN-US. Hit enter to keep it or choose a different one:


By default, I will install everything at /home/razo/.ies4linux
I will also install Flash 9 plugin and create Desktop shortcuts.
Is that ok for you? (To configure advanced options type n) [ y / n ] n

Should I install Adobe Flash 9 plugin? [ y / n ] y

And how about Desktop icons? Can I create them? [ y / n ] y

Everything will be installed at /home/razo/.ies4linux
Hit enter to keep this or type the new folder (absolute path):


Binary launchers will be created at /home/razo/bin
Hit enter to keep this or type the new folder:


We'll use wget to download files. If you need some special flag (proxy,...), type them now:


All right! Let's start the installations...

Downloading everything we need
  DCOM98.EXE
  mfc40.cab
  249973USA8.exe
  ADVAUTH.CAB
  CRLUPD.CAB
  HHUPD.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IEDOM.CAB
  IE_EXTRA.CAB
  IE_S1.CAB
  IE_S2.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S5.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S4.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S3.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S6.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  SCR56EN.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  SETUPW95.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  FONTCORE.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  FONTSUP.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  VGX.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  swflash.cab
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Cannot download flash

what can i do??

---

### Post by _lynX on 2006-10-30
You may need to install the cabextract package.

*sudo aptitude install cabextract*

Hopefully that helps.

---

### Post by Nut on 2006-10-30
why would you install ie anyway? it sucks. it reads css incorrectly, as well as html. it's slower to loading. occupies more of the computer process load opening it and reading the file's coding too.

---

### Post by tronica on 2006-10-30
for anyone interested heres an easy to use IE on linux. Includes verions 5 through 6.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by llamakc on 2006-10-30
Because the OP wants to, and can.

Are you behind a proxy?

---

### Post by razo559 on 2006-10-30
i already installed cabextract this is what i get when i tell it not to install flash::

Wine 0.9.9
Wine 0.9.9
Wine 0.9.9
Welcome, razo! I'm IEs4Linux.
I can install IE 6, 5.5 and 5.0 for you easily and quickly.
You are just four 'enter's away from your IEs.

I'll ask you some questions now. Just answer y or n (default answer is the bold one)

IE 6 will be installed automatically.
Do you want to install IE 5.5 SP2 too? [ y / n ]

And do you want to install IE 5.01 SP2? [ y / n ]

IEs can be installed using one of the following locales:
EN-US PT-BR DE FR ES IT NL SV JA KO NO
DA CN TW FI PL HU AR HE CS PT RU EL TR
Default is EN-US. Hit enter to keep it or choose a different one:


By default, I will install everything at /home/razo/.ies4linux
I will also install Flash 9 plugin and create Desktop shortcuts.
Is that ok for you? (To configure advanced options type n) [ y / n ] n

Should I install Adobe Flash 9 plugin? [ y / n ] n

And how about Desktop icons? Can I create them? [ y / n ]

Everything will be installed at /home/razo/.ies4linux
Hit enter to keep this or type the new folder (absolute path):


Binary launchers will be created at /home/razo/bin
Hit enter to keep this or type the new folder:


We'll use wget to download files. If you need some special flag (proxy,...), type them now:


All right! Let's start the installations...

Downloading everything we need
  DCOM98.EXE
  mfc40.cab
  249973USA8.exe
  ADVAUTH.CAB
  CRLUPD.CAB
  HHUPD.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IEDOM.CAB
  IE_EXTRA.CAB
  IE_S1.CAB
  IE_S2.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S5.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S4.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S3.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  IE_S6.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  SCR56EN.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  SETUPW95.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  FONTCORE.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  FONTSUP.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
  VGX.CAB
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/razo/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/razo/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/razo/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; file possibly truncated by 542575 bytes.
/home/razo/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: no valid cabinets found
/home/razo/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_EXTRA.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; file possibly truncated by 268207 bytes.
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: no valid cabinets found
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: no valid cabinets found
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: no valid cabinets found
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: no valid cabinets found
/home/razo/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: no valid cabinets found
/home/razo/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: no valid cabinets found
/home/razo/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: no valid cabinets found/home/razo/.ies4linux/downloads/ie6/EN-US//VGX.CAB: no valid cabinets found
An error occured when trying to cabextract some files.

---

### Post by razo559 on 2006-10-30
how do i find out if im behind a proxy??

---

### Post by razo559 on 2006-10-30
how can i configure wget???

---

### Post by smithveg on 2006-11-11
> **razo559 said:**
> 
An error occured when trying to cabextract some files.


razo559,

I faced the same error, what's will caused this? I can't figure out.
Someone helps?

---

### Post by mstrat on 2006-11-15
SAME PROBLEM with me...Please help.  I have to use one website and the ONLY way it will work is with Internet Explorer...without it I must keep XP on my computer...THAT is what sucks.  I even went straight to the source of the website and they said that it wasn't worth their time to reprogram their site for the small percent of us that don't use Internet Explorer...

---

### Post by smithveg on 2006-11-15
Hi,

After i install 'cabextract-1.2.tar.gz' and 'ies4linux-2.1beta3.tar.gz'
Magically the IE was installed successfully, and it create an icon on desktop.

Try to search for this two package, if really can not work. Give me your email i sent it to you. Because i lost the thread, i do not remember which thread helps me in this forum. Sorry for that.

Hope my reply would helps.

---

### Post by mstrat on 2006-11-15
GOT IT!!!!!

When it asks you to install 5.5 SP2 say NO along with 5.01 SP2 say NO

Then it worked perfectly!!!!!!!!!!!

---

### Post by smithveg on 2006-11-15
REally? I don't think so. Because i might select yes for both of them. Anyway, good to hear that you are ok now. :)

---

### Post by mstrat on 2006-11-15
Yeah, I'm not sure if it's the best way for everyone, thought it DID work for me...just another suggestion, I didn't need 3 versions on my computer, just 6 to get me through with the ONE website that was causing me to get more gray hairs and loose the few I have left!

---

### Post by Velotix on 2006-11-15
Looks like this problem's been solved, but for future reference I'll let you know that you've probably wasted your time downloading it.

Generally, if a webpage only works with a certain browser, that's only because the webpage checks which browser you're using before it will load, and if it doesn't find the intended browser, it locks you out of the page.

The trick, then, is to fool the page into thinking you're running IE. I recall an extension in Firefox that permits such trickery, but I have no idea if the plugin's Windows-only nor can I remember its name offhand.

Another option is to get the IETab extension for Firefox, which makes a page load in Firefox but using the IE rendering engine, which is useful for web developers and you from the sounds of it. Again, I don't know if it's Windows-only, but I couldn't find it when I looked for it. :(

Take a look, though, it might save you a lot of grief.

---

### Post by mstrat on 2006-11-15
I have that installed in Foxfire, I also don't remember where or how, but even when I set it to render as IE, that site doesn't work properly.  It doesn't lock me out, it is a Real Estate search site that I use as a Realtor, and this is the only success that I have had.  I still have one obstacle to overcome before I can be "XP Free"...it is a palm Tungsten 5 that I need to hotsync and get an update through the internet...with a specific program through GE Securities, it updates my Supra Key that opens lockboxes.  If you have any assistance with that I'd sure like it!

---

### Post by smithveg on 2006-11-15
> **Velotix said:**
> 
The trick, then, is to fool the page into thinking you're running IE. I recall an extension in Firefox that permits such trickery, but I have no idea if the plugin's Windows-only nor can I remember its name offhand.


I agree with you. I heard this extension somewhere in this forums. But i do not remember that name. If someone can give a correct name or package url. That's an appreciated job. Thanks.

---

### Post by halitech on 2006-11-15
I think it's something along the lines of agent user switcher or something like that.

---

### Post by FattyCNS on 2006-11-17
> I heard this extension somewhere in this forums. But i do not remember that name. If someone can give a correct name or package url.


The extension you're after is "User Agent Switcher"

[https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

> Another option is to get the IETab extension for Firefox, which makes a page load in Firefox but using the IE rendering engine, which is useful for web developers

IETab is a great extension but is windows only as you need IE installed for it to work.

---

### Post by smithveg on 2006-11-18
Cool, That's what we looking for. Thank.

smithveg

---

