---
title: "Mozilla ActiveX control"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-03-11
I am trying to run counterstrike 1.6 on ubuntu using [this how to]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games")
But I am to noob for section 3, mozilla activeX control
Just don't know how to install, and don't have a clue of how I should save it in my C on wine...
Could someone please Make step 3.1 easier, for real noobs :D

Grtz PingunZ

---

### Post by chuckyp on 2006-03-11
Well download the file they mention.  Then you need to extract it i.e. tar xvzf mozcontrol.tar.gz.   Then move the folder it extracted to /home/<username>/.wine/drive_c/Progra\ Files/  with "mv" then you cd into that folder and run the regsv32 mozctlx.dll.   That way you will have working fonts in steam.

Keep in mind the .wine directory is hidden because of the leading "."  So you won't be able to see it in a file browser from within gnome.  You will have to do this via terminal.

---

### Post by PingunZ on 2006-03-11
How to do this in console, sorry for stupid questions :p
Still learning :)

Grtz PingunZ

---

### Post by chuckyp on 2006-03-11
Well to download the file you would type:
wget [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)

Then change directory to the program files directory:
cd .wine/drive_c/Program\ Files/

Now to extract it:
tar xvzf ~/mozcontrol.tgz

Now change directory tot he mozcontrol folder:
cd mozcontrol

Then type the regsv32 command to register the dll with wine:
regsvr32 mozctlx.dll

Should be good to go then.  And fonts will work with steam.  A quick tip after doing this to enter your username in pass in steam you have to right click in the text field then click in it.  Type in your username.  Its a bug with windows focus wine and steam.  After you get your username and pass entered check the remember password box so you don't have to do this again.

Another way around this is to run winecfg and select emulate virtual desktop then run steam.  Enter your user and pass close it.  Run winecfg and uncheck virtual desktop.  Restart steam and download cs.

---

### Post by PingunZ on 2006-03-11
[QUOTE=chuckyp]Well to download the file you would type:
wget [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)
[/QUOTE]

console : Connecting to downloads.transgaming.com|67.19.190.68|:80... verbonden.&#8629;
HTTP verzoek verzonden, wacht op antwoord... 404 Not Found
14:44:14 FOUT 404: Not Found.

Doesn't seem to work :s Ty for the effort anyway

Grtz PingunZ

---

### Post by stalefries on 2006-03-11
404 means the file was not found. Apparently, it isn't there anymore.

---

### Post by PingunZ on 2006-03-11
Ok its working now, only need to get the tahoma.ttf font in the windows font directory ( “~/.wine/drive_c/windows/fonts/”  )
I got it downloaded, but I don't know how tu unpack it in that folder
If someone could help me out I would be able to game on ubuntu and I could finally delete windows :)

Grtz PingunZ

---

### Post by PingunZ on 2006-03-11
Nobody ?

Grtz PingunZ

---

### Post by pAuthority on 2006-06-17
Hi, i'm a beginner also. I managed to install Steam and Red Orchestra on my Kubuntu via wine, the trouble is that i'm getting an error message 
"wine: Call from 0x7fc31600 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting"

I used the great Steam HOWTO in [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)
I have installed the Mozilla ActiveX controls, and registered the plugin, but one thing I don't have a clue, is how to remove old ActiveX? Step 3 in that howto says that I should first remove old versions and then install the new one, but how?

---

