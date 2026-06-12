---
title: "How do I install my Network printer?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-01-21
How do I install my Network printer that's connected to the router?  I did it once for Windows XP by installing the UNIX printer driver instead of using a for Windows printing driver, but I'm not sure what to do under Linux.
This is as far as I could get
[http://ubuntuguide.org/wiki/Dapper#Print_Server_.28cupsd.29](http://ubuntuguide.org/wiki/Dapper#Print_Server_.28cupsd.29)

---

### Post by kingmonkey on 2007-01-21
Go to [http://localhost:631/](http://localhost:631/)

Add printer

then point to the IP address of your printer

---

### Post by jingo811 on 2007-01-21
Eh isn't there a local way to install my home router printer?  I don't feel very comfortable giving away my router login/password out on the Internet :confused:

Never mind I solved it locally.  I just selected the LPR or LPD printer option on the setup page.  And then typed my routers ip adress where it said location or something like that.  192.168.0.1 for my Netgear router.
Must say I'm impressed it went quicker and smoother than installing on Windows XP :-) Didn't even need the hassle of taking out the OS CD to install drivers.

---

### Post by kingmonkey on 2007-01-23
Sorry I should have explained a bit more.

localhost:631 is the local setup for CUPS which is the thing that controls printers.

---

### Post by gsparky2004 on 2007-03-25
FYI, the localhost:631 option worked perfectly when installing my networked HP Photosmart P1000 printer using a DLink DP-311U print server.  For those of you new to Linux (as I am!), here's how:

*  Open your web browser and type in "http://localhost:631" into your address box.
*  Click on the "Add Printer" button.
*  On the "Add New Printer" page, enter the following information:
  - Name: <name for your printer, BUT DON'T USE ANY SPACES!  For example, mine is simply "HP1000">
  - Location:  Doesn't matter.  Leave blank, if you want.  Or enter the location of Jimmy Hoffa's body, for that matter.  Yer choice.
  - Description:  Doesn't matter.  I entered the full name of my printer, which is "Photosmart P1000".
*  Click "Continue"
*  You should now see a box marked "Device".  It's a drop-down menu.  Since I'm using a DLink print server, I chose "LPD/LPR Host or Printer".  You may have a different device.
*  Click "Continue"
*  You should see a box named "Device URI".  Again, if you're using a DLink 311U (as I am), type in "socket://<DLink IP address>.  For example, the IP address of my DLink is 192.168.100.55.  So, I typed in "socket://192.168.100.55".
*  Click "Continue"
*  You now need to enter the manufacturer of your printer.  I scrolled down and selected "HP".
*  Click "Continue"
*  Yet another page that might trip you up.  You need to select the particular model of your printer.  The problem is that there are several models of "HP Photosmart P1000" listed.  I selected the "HP Photosmart P1000 Foomatic/hpijs (recommended) (en)".  There seems to be one that is "recommended" for each model.  I suggest going with that for the first try.  If it doesn't work, you will have to try others.
*  Click "Add Printer"
*  If everything works, you should see a message such as, "HP1000 successfully added!"

You should see a tab along the top of the page that says, "Printer".  Select that, then look for a button "Print Test Page".  If you press that button and get a proper print-out, you're set!

Hope this helps!

Gary

---

### Post by mkclarke on 2007-07-18
You gotta be kiddin' me!!  I just followed the steps posted by gsparky2004 for my setup, and it worked!  I figured I was wasting my time because I have a Dell branded printer (Lexmark) connected to my Apple Airport Extreme wireless router.  But it worked first try.  Like you said, quicker than in Windows!  I had to install the Bonjour printer wizard to install it in Windows.

I'm likin' this Linux stuff!

Thanks again for your awesome tip!

Mike

---

### Post by iheartubuntu on 2008-02-21
Ive tried this with no luck at all. I get to the point where I input 192.168.1.1 or 192.168.0.1 and right before adding the printer it asked for my username and password.. of what, the router? So I inputed that, but think it was the wrong password and now anytime I try to install the printer, it doesnt ask me for the username and password anymore.

Please help! Thanks!

> **gsparky2004 said:**
> FYI, the localhost:631 option worked perfectly when installing my networked HP Photosmart P1000 printer using a DLink DP-311U print server.  For those of you new to Linux (as I am!), here's how:

*  Open your web browser and type in "http://localhost:631" into your address box.
*  Click on the "Add Printer" button.
*  On the "Add New Printer" page, enter the following information:
  - Name: <name for your printer, BUT DON'T USE ANY SPACES!  For example, mine is simply "HP1000">
  - Location:  Doesn't matter.  Leave blank, if you want.  Or enter the location of Jimmy Hoffa's body, for that matter.  Yer choice.
  - Description:  Doesn't matter.  I entered the full name of my printer, which is "Photosmart P1000".
*  Click "Continue"
*  You should now see a box marked "Device".  It's a drop-down menu.  Since I'm using a DLink print server, I chose "LPD/LPR Host or Printer".  You may have a different device.
*  Click "Continue"
*  You should see a box named "Device URI".  Again, if you're using a DLink 311U (as I am), type in "socket://<DLink IP address>.  For example, the IP address of my DLink is 192.168.100.55.  So, I typed in "socket://192.168.100.55".
*  Click "Continue"
*  You now need to enter the manufacturer of your printer.  I scrolled down and selected "HP".
*  Click "Continue"
*  Yet another page that might trip you up.  You need to select the particular model of your printer.  The problem is that there are several models of "HP Photosmart P1000" listed.  I selected the "HP Photosmart P1000 Foomatic/hpijs (recommended) (en)".  There seems to be one that is "recommended" for each model.  I suggest going with that for the first try.  If it doesn't work, you will have to try others.
*  Click "Add Printer"
*  If everything works, you should see a message such as, "HP1000 successfully added!"

You should see a tab along the top of the page that says, "Printer".  Select that, then look for a button "Print Test Page".  If you press that button and get a proper print-out, you're set!

Hope this helps!

Gary

---

