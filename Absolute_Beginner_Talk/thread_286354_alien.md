---
title: "alien"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-10-27
hi, I am trying to use alien to change a package from .rpm to .deb.  My question is, does the package have to be saved in a certain spot?  I ask this because I followed the commands that are in some instructions and it says the package can not be found.

---

### Post by meng on 2006-10-27
No it does not have to be saved in a particular spot. But it helps if you happen to be in the same directory as the .deb file when you run dpkg. Either the instructions are no good, or you're not following them properly.

---

### Post by Rackerz on 2006-10-27
You need to change to the directory the rpm is in to be able to convert it.

---

### Post by DevNull11 on 2006-10-27
You should be able to type the path tho the .rpm.

---

### Post by familyjules74123 on 2006-10-28
this is what I get when I try to convert the file to debian:

> mike@mike-laptop:~$ sudo alien -k bitpim-0.9.07-0.i386.rpm
Password:
File "bitpim-0.9.07-0.i386.rpm" not found.


That is the right name of the file too, I copy and pasted it from the file itself.

---

### Post by Marsolin on 2006-10-28
[Here]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien") is a recent howto article.

---

### Post by dbott67 on 2006-10-28
> **familyjules74123 said:**
> this is what I get when I try to convert the file to debian:



That is the right name of the file too, I copy and pasted it from the file itself.

Make sure you're in the correct working directory where the rpm is.  You can use **ls -all** to list all the files in the directory and make sure that you see it listed.

Type the **sudo alien -k** command and the first few letters of the file, followed by the TAB key.
```
sudo alien -k bit*[COLOR="Red"]<press tab> the system should complete the name for you[/COLOR]*
```
```
sudo alien -k bit**[COLOR="Red"]pim-0.9.07-0.i386.rpm[/COLOR]**
```

-Dave

---

### Post by familyjules74123 on 2006-11-02
OK, it worked and said that it installed and everything, now this may be a very dumb, rookie question, but how do I run it now? I can't seem to figure it out.

---

### Post by mahy on 2006-11-02
sudo dpkg -i *packagename*.deb

---

### Post by familyjules74123 on 2006-11-02
> mike@mike-laptop:~$ sudo dpkg -i bitpim_0.9.07-0_i386.deb
Password:
(Reading database ... 94472 files and directories currently installed.)
Preparing to replace bitpim 0.9.07-0 (using bitpim_0.9.07-0_i386.deb) ...
Unpacking replacement bitpim ...
Setting up bitpim (0.9.07-0) ...

It does that with that package, but the program itself doesnt open, I would like to know how to run the program itself is what I am asking, also if there is a way to create a desktop launcher for it through the terminal.

---

### Post by dbott67 on 2006-11-03
The command **sudo dpkg -i bitpim_0.9.07-0_i386.deb** *installs* the package.  To run the package, you must run the executable (or the shell script, whichever the case may be).

In this case, it may be as simple as typing the command **bitpim** from a terminal (you may have to cd to the bitpim directory) or you can type **slocate bitpim** to help track down the location of the executable.

If you're still have trouble running the app, post back here.

-Dave

---

### Post by dbott67 on 2006-11-03
I just checked out the Debian package files for bitpim & this is a listing of all files:
```
etc/udev/bitpim.rules					    comm/bitpim
lib/udev/notify-bitpim					    comm/bitpim
usr/bin/bitfling					    comm/bitpim
**[COLOR="Red"]usr/bin/bitpim[/COLOR]**						    comm/bitpim
usr/share/applications/bitpim.desktop			    comm/bitpim
usr/share/bitpim/code/DSV				    comm/bitpim
usr/share/bitpim/code/aggregatedisplay.py		    comm/bitpim
usr/share/bitpim/code/analyser.py			    comm/bitpim
usr/share/bitpim/code/auto_sync.py			    comm/bitpim
usr/share/bitpim/code/bitfling/__init__.py		    comm/bitpim
usr/share/bitpim/code/bitfling/bitfling.py		    comm/bitpim
usr/share/bitpim/code/bitfling/client.py		    comm/bitpim
usr/share/bitpim/code/bitfling/guihelper.py		    comm/bitpim
usr/share/bitpim/code/bitfling/version.py		    comm/bitpim
usr/share/bitpim/code/bitfling/xmlrpcstuff.py		    comm/bitpim
usr/share/bitpim/code/bitflingscan.py			    comm/bitpim
usr/share/bitpim/code/bp.py				    comm/bitpim
usr/share/bitpim/code/bp_obex.py			    comm/bitpim
usr/share/bitpim/code/bpcalendar.py			    comm/bitpim
usr/share/bitpim/code/bphtml.py				    comm/bitpim
usr/share/bitpim/code/bptime.py				    comm/bitpim
usr/share/bitpim/code/brewcompressedimage.py		    comm/bitpim
usr/share/bitpim/code/calendarcontrol.py		    comm/bitpim
usr/share/bitpim/code/calendarentryeditor.py		    comm/bitpim
usr/share/bitpim/code/call_history.py			    comm/bitpim
usr/share/bitpim/code/call_history_export.py		    comm/bitpim
usr/share/bitpim/code/comdiagnose.py			    comm/bitpim
usr/share/bitpim/code/comm_notify.py			    comm/bitpim
usr/share/bitpim/code/common.py				    comm/bitpim
usr/share/bitpim/code/common_calendar.py		    comm/bitpim
usr/share/bitpim/code/commport.py			    comm/bitpim
usr/share/bitpim/code/comscan.py			    comm/bitpim
usr/share/bitpim/code/conversions.py			    comm/bitpim
usr/share/bitpim/code/csv_calendar.py			    comm/bitpim
usr/share/bitpim/code/data_recording.py			    comm/bitpim
usr/share/bitpim/code/database.py			    comm/bitpim
usr/share/bitpim/code/developer.py			    comm/bitpim
usr/share/bitpim/code/field_color.py			    comm/bitpim
usr/share/bitpim/code/fileinfo.py			    comm/bitpim
usr/share/bitpim/code/filesystem.py			    comm/bitpim
usr/share/bitpim/code/fileview.py			    comm/bitpim
usr/share/bitpim/code/fixedscrolledpanel.py		    comm/bitpim
usr/share/bitpim/code/fixedwxpTag.py			    comm/bitpim
usr/share/bitpim/code/gcal_calendar.py			    comm/bitpim
usr/share/bitpim/code/gui.py				    comm/bitpim
usr/share/bitpim/code/guihelper.py			    comm/bitpim
usr/share/bitpim/code/guiwidgets.py			    comm/bitpim
usr/share/bitpim/code/helpids.py			    comm/bitpim
usr/share/bitpim/code/hexeditor.py			    comm/bitpim
usr/share/bitpim/code/ical_calendar.py			    comm/bitpim
```

It looks like the binary (i.e. executable) is in /usr/bin, which means that you should just be able to type in 'bitpim' from the command line.  If that works, you can create a link on your desktop that points to that executable).

-Dave

---

