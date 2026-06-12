---
title: "Print Command"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-03
How do I find out what command is used to send a job to my printer?  It is not lpr or lp.  

The printer is an HP LaserJet 1200 and the URI is [http://192.168.16.240:631](http://192.168.16.240:631) (from CUPS).  It works but I need to find out the print command to put into the xsane setup ....

---

### Post by jfinkels on 2007-10-04
Are you sure it's not lpr? Something like "lpr -P xxx"?

---

### Post by expatCM on 2007-10-06
don't think so ....  but perhaps I am wrong ....

I have tried the following - 

lpr -P 192.168.16.240:631   (being the location of the printer) 

lpr -P HPLaserJet  (being the description of the printer)

lpr -P Laserjet-1200  (being the system / administration / printing / properties name of the printer)

use of these does not give a message of pipe broken but it also does not print.

---

### Post by dwhitney67 on 2007-10-06
It's [FONT="Courier New"]lp -d <printerQueueName> <file ...>[/FONT]

The -d is used to specify the destination.  This can be made superfluous by designating a "default" printer on your system, or by defining an environment variable called LPDEST or PRINTER for the print queue of your choice.  In such cases, the command would then be:

[FONT="Courier New"]lp <file ...>[/FONT]

You can list the printer queue(s) on your system with this command:

[FONT="Courier New"]$ lpstat -a[/FONT]

The first field shows the printer queue name.

---

### Post by expatCM on 2007-10-06
then I am really missing the point .....   I have tried all of the following settings in xsane for the printer

lp default
lpr default
lp -d Laserjet-1200
lpr -d Laserjet-1200
lp -d 192.168.16.240
lpr -d 192.168.16.240

and they all return "Broken Pipe".

lpstat -a
LaserJet-1200 accepting requests since Wed 25 Jul 2007 05:21:02 PM ICT

I never seem to see the printer icon for the print queue appear in the system tray with xsane.

---

### Post by dwhitney67 on 2007-10-06
It would appear, at first glance, that something is afoul with your setup of LaserJet-1200.  Perhaps it might be best to set it up again, or just to verify its configuration settings.

Using your browser, you can manage your printer(s) that were setup using CUPS.  Just type or click on this URL: [ http://localhost:631]("http://localhost:631/")

---

### Post by expatCM on 2007-10-06
The printer works from every other application which makes me more than a little curious ....

The localhost:631 does open the CUPS front end and the printer is there and apparently correctly identified.

Is there anything in particular I should look for?

or is there an alternative way of setting up the printer which I may have overlooked or not got right?

---

### Post by dwhitney67 on 2007-10-06
I did a Google search and I came across this [thread]("http://lists.alioth.debian.org/pipermail/sane-devel/2006-June/017166.html"), and then the [follow-up thread]("http://lists.alioth.debian.org/pipermail/sane-devel/2006-June/017184.html") with a solution.

From your earlier posts, I saw that you had experimented using 'lpr'.  Can you please try one more time specifying it using the following command line parameter:

[FONT="Courier New"]lpr -P LaserJet-1200[/FONT]

Note that unlike with 'lp', with 'lpr' the destination printer is specified with a -P option, not -d.  For more information on 'lpr', run this command:

[FONT="Courier New"]$ man lpr[/FONT]

---

### Post by expatCM on 2007-10-07
Thank you for your continued help ...  :)

I tried lpr -P LaserJet-1200 and nothing happened but I did not get a broken pipe message.

So I had a go with 

lpr -P HP and lpr -P hp

lpr -H 192.168.16.240:631

lp -d hp

which all gave broken pipe messages.  I seem to have more success with lpr than lp since the errors either are slower to appear or do not come.  lp is to the point ... no go.

I wonder if I should wait for a couple of weeks and see if Gutsy has this sorted .....

---

### Post by dwhitney67 on 2007-10-07
Try to test lpr from the command line to see if it works.  If it does, then you can eliminate that command as a suspect.  Try:

[FONT="Courier New"]$ lpr -P LaserJet-1200 /etc/motd[/FONT]

Also, confirm that your printer is setup as the default:

[FONT="Courier New"]$ lpstat -d[/FONT]

If it is, then there is no need to specify the -P option with lpr (or the -d option with lp).

---

### Post by expatCM on 2007-10-07
life now gets interesting ....

lpr -P LaserJet-1200 /etc/motd
first returned a Broken Pipe error message (and Failed to execute printer command) and much to my surprise a page was printed.  It was not a copy of what was on the scan bed, it was three short paragraphs as follows - 

> Linux P4P800X 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686

The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

I was so surprised that I did it again and the same message was printed again.  The date is wrong so it is not the system date ......  but goodness ... something printed....

Next ......

lpstat -d
no system default destination

So I just went to System / Administration / Printing and set the only printer as default (thought it would have been with there being only one printer but not so).  There is now a big green tick across it ...

With this extra information I then went back to settings and changed the printer back to lpr only.  I scanned a job and no errors.  This time the print spooler icon has appeared in the system tray. Nothing was printed but the printer appeared to receive a job (or at least the light flashed for a while) and then nothing ....  no printed page.

---

### Post by runemaste644 on 2007-10-07
If you want to have some fun with that, force a paper jam and it will say "Printer on fire!":lolflag:


No, seriously, it will say that.

---

### Post by dwhitney67 on 2007-10-07
Don't be concerned with the message that was printed.  I merely suggested that you print a file... any file... and the one I provided as an exampled was the "message of the day" file, which most Unix/Linux systems include within /etc/motd.

Many sys admins change the /etc/motd file to include their custom message so that when user's log in from a remote location, it is displayed to them with "informative" information.

Also, at any time you want to peruse all information about your printer(s), the following command will work:

$ lpstat -t

Back to your problem... I have a scanner, but I am too lazy to hook it up to my system right now.  I do have xsane installed but unlike you, I am running Ubuntu 7.04 Feisty.  Btw, I am running version 0.994 of xsane.  Here's the command I ran to determine that; also note the other info, namely the output formats:

```
$ xsane --version
xsane-0.994 (c) 1998-2007 Oliver Rauch
  E-mail: Oliver.Rauch@xsane.org
  package xsane-0.994
  compiled with GTK-2.10.11
  without GIMP support
  XSane output formats: jpeg, pdf(compr.), png, pnm, ps(compr.), tiff, txt
```

If you are able to print from the command line, but not from xsane, then I would focus the attention on xsane.  I wish I could help more, but I have reached the end of my knowledge-chain.  Even if I were to connect my scanner to my system, and it were to succeed or fail, I would not be able to offer you reasons as to why.

P.S.  Do you have Ghostscript installed on your system?  Maybe, and this is a long stretch, if you do not have it installed, that is causing the problems.  Here's a [link]("https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/114866") on what "rjonnal" (look for his post) did to install the real ghostscript.

---

