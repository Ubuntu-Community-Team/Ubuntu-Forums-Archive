---
title: "Tried to setup wireless card...now can't boot up"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by chris_n00b on 2007-06-12
Hey all. I'm running 6.06 still on my box and was trying to setup a Linksys wireless card the other day to work with my router. Anyway, I was looking in this post....

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#auto]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#auto")

in section 3.2, since my linksys router is running WPA encryption. I was following those steps to edit that conf file or whatever it is and I still couldn't connect to the internet. ( i didn't back up that file before editing since im very new to this and a dumb@$$ ) now when I tried to restart I can't boot up. How can I return that file to its original state? ( then I have to figure out how to get this wireless card to work)


I had to boot up and hit something a while ago to use the terminal to revert a file, but it was something I had made a copy of so fairly simple. Now Im not sure what to do... :(

---

### Post by Borzo on 2007-06-13
you didn't describe when does it stop booting, after grub?, does it show the ubuntu logo, progress bar?

---

### Post by chris_n00b on 2007-06-13
Yes, it starts to boot, gets to the Ubuntu logo where the progress bar is, (when it does the checks and puts 'OK' after each.)  But when it gets to ,I believe, network connections or that network one it freezes. I found last night that if I press PrtScrn when its frozen it bypasses it and marks that one failed then checks the rest which are all ok. Then I type my username and login password and I just get a black screen.

---

### Post by Borzo on 2007-06-13
see if you can log into with the console, at the login screen press ctrl+alt+F1 and try to login, you can check your system logs in /var/logs from there if you manage to login this way.

---

### Post by chris_n00b on 2007-06-13
I hit ctrl+alt+f1 on the login screen and it went to the dos lookin screen ( terminal? ) and went through the motions... got stuck on the network interfaces one. I hit prntscrn and it 'failed' it and bypassed it then let me log in with my username and password.

Now I'm at the prompt.  What should I try?

EDIT* I belive the command to edit that file was

> gksudo gedit /etc/network/interfaces

EDIT 2*  When I type in that command, it says ' Gtk-WARNING **: cannot open display:
Then gives me another prompt.


How do I revert that network interface file back to original?

---

### Post by chris_n00b on 2007-06-14
bumpity bump :)

---

### Post by Austin_KW on 2007-06-14
If you remove the "auto ra0" it should not start the wireless interface on boot.

Try that and then post your /etc/network/interfaces and we can see what is wrong with it.

---

### Post by drummer on 2007-06-14
to edit the file, you can't use gedit because there's no X server running (the GUI); that's what the error message is saying, it can't connect to the GUI to draw the gedit window. You'll have to use a different text editor, I'd try pico.
```
sudo pico /etc/network/interfaces
```
then save and close the file with Control+O, Control+X

As for how to fix the problem, I'd probably comment out the added lines in the interfaces file and then execute them in the terminal one at a time (without the 'pre-up', that's a specific word for the interfaces file) to see where it's getting stuck and hanging. (remember to prepend each of those commands with 'sudo').

---

### Post by chris_n00b on 2007-06-23
well i've been trying to fix this but cant figure it out. When I log in using Ctl+Alt+F1 (then typing in my username and pass) then try ```
sudo pico /etc/network/interfaces
``` but nothing happens. Just goes to a new line.  I just bought a book on Ubuntu Linux which has a lot of info, but I can't seem to reedit the file.

I typed ```
vi /etc/network/interfaces
```and the file displays but I guess I can't edit it becuase its a read only file?

Alll I  need to do is make the file at /etc/network/interfaces back to original so I can start over from scratch to try to get my wireless card to work.

---

### Post by pepsi_max2k on 2007-06-23
"sudo vi /etc/network/interfaces"

hit "i" to enter insert mode, up/down/left/right, backspace, esc, ":wq!" to save. that should do it. and fwiw, what's in your interfaces file? i have a similar problem :(

---

### Post by drummer on 2007-06-23
Are you sure you didn't make a typo? If the file opens in vi, it should be opening in pico. You can also edit it in vi, just add a 'sudo' to that command.

---

### Post by chris_n00b on 2007-06-23
when I type in this exactly   ```
sudo vi etc/network/interfaces
```

or

```
sudo pico /etc/network/interfaces
```

then hit enter or return I just goes to a new line. no prompt no loading anything, nothing. Is it that I messed up the driver that it wont boot to the GUI?

---

### Post by chris_n00b on 2007-07-12
Does anyone know what I should try next? Can I try to just put in the live cd and somehow restore that file?

During boot up can I somehow 'blacklist' that file so I can at least get into the OS and them go in to reedit the file that way?  This sucks not being able to even use the computer now for like 3 weeks + .......

Should I post a video of what its doing or something?

---

### Post by twiceasworn on 2007-07-12
Regardless of whether you hosed the gui the terminal based text editors should be working without an issue.  You said you were able to get into vi before but you couldn't edit.  When you type ```
sudo vi /some/path/here
``` it doesn't do anything?  That does not really make any sense.  I am fairly sure if you can get into vi without the sudo then you can do :wq! to force it to write the file.  At least this worked for me the other day.

---

### Post by chris_n00b on 2007-07-12
Oh... no when I type sudo vi etc... It goes into the file. I'm just not sure the correct procedure to edit it and save it.

Basically what I want to know is:

1.  Once I get into the file, do I just cursor up and down to edit stuff? What's this :wq! command? (I couldn't seem to edit it before... It was not like just basic typing; there were ^M things being added and wierd characters etc...) And then if I do get it back... What is the command to properly save and exit/ restart?

2. Could some one post the default network interface file so I know what to change it back to?  Otherwise I can just load the live cd into my windows computer and look at it on there....

Hope this all makes sense.

> **twiceasworn said:**
> Regardless of whether you hosed the gui the terminal based text editors should be working without an issue.  You said you were able to get into vi before but you couldn't edit.  When you type ```
sudo vi /some/path/here
``` it doesn't do anything?  That does not really make any sense.  I am fairly sure if you can get into vi without the sudo then you can do :wq! to force it to write the file.  At least this worked for me the other day.

---

### Post by Austin_KW on 2007-07-12
vi will not make any sense to you, unless you used line editors 20 years ago. It is a visual Interface to an old line editor.

try "sudo nano /some/path/here" make your changes and ctrl-x to exit

FYI; for vi
use the cursor to move around (in command mode) enter "i" to insert text and then the escape key to get back to command mode.
"dd" in command mode deletes the current line
typing ":wq!" in command mode is write,quit,forced.

---

### Post by Austin_KW on 2007-07-12
The default interfaces file will usually have an entry for the loopback (loopback address) and first ethernet (dhcp address) interfaces

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

```

---

### Post by Al3xK3aton on 2007-07-12
Try switching from the linksys software to controlling it directly by the linux networking. The linksys networking software is notoriously sucky.

---

### Post by chris_n00b on 2007-07-12
Yes, that was what I was doing. I threw in the lynsys card then went in to the networkin control section. It recognized it, but I couldn't get online. I was reading on here for instructions, but changed that file and, thus now I can't boot up.  Once I get home after work I will attack this problem again.

> **Al3xK3aton said:**
> Try switching from the linksys software to controlling it directly by the linux networking. The linksys networking software is notoriously sucky.

---

### Post by chris_n00b on 2007-07-12
> **Austin_KW said:**
> vi will not make any sense to you, unless you used line editors 20 years ago. It is a visual Interface to an old line editor.

try "sudo nano /some/path/here" make your changes and ctrl-x to exit



Thanks for the feedback. I will try this tonight. Although everything I have tried just leads me to a new line. (no prompt or anything, just goes to a new line with flashing cursor and I can't do anything.) I don't think I have tried sudo nano yet so I will try that tonight. 

thanks.

_chris

---

### Post by ugm6hr on 2007-07-12
The other option would be to just boot from the LiveCD (or any other Linux LiveCD), and access the file on the hard drive to edit it there.

---

### Post by chris_n00b on 2007-07-12
But if you're running off the live cd wouldn't you just be accesing the CD? and not your installation on your harddrive?

---

### Post by Al3xK3aton on 2007-07-12
Can you copy the live CD to a CDRW?

---

### Post by chris_n00b on 2007-07-12
Well actually heres the update since im now home and looking at it. sudo nano or pico gedit, nothing will bring up the file.  

I type vi /etc/network/interfaces

and I get the file to come up.  I see i have like 4 or 5 extra lines of text in there i have to delete to get it back to normal.  When I use the command 'dd' from there it says

Warning you are editing a read only file.  and basically wont let the changed be saved.  Then it tells me:

Found a swap file by the name " var/tmp/interfaces.swp"
file name: /etc/network/interfaces
Modified: YES

and some other stuff about the date and so forth.  Is this the temp file that was auto created? 


Anyway it gives me two 'points' to consider

(1)  Another program may be editing this same file.  If thats the case be careful not to end of with two different files of the same type etc... proceed with caution etc..

(2) an edit session for this file crashed. If this is the case use ' :recover '   or " vim -r /etc/network/interfaces" to recover the changes.If you did this already delete the swap file " var/tmp/interfaces.swp" to avoid this message.

---

### Post by chris_n00b on 2007-07-12
also when I delete those extra lines and use 

:w to write it says read only use ! to override

so I do :w!

and it says cannot open file for writing.

---

### Post by Austin_KW on 2007-07-12
You need to type "sudo vi" i.e run vi as root or you will not have write permission

---

### Post by chris_n00b on 2007-07-12
> **Austin_KW said:**
> You need to type "sudo vi" i.e run vi as root or you will not have write permission


That seems to be the prob.  Everytime I type 'sudo' first it just goes to a new line and i can' tdo anything else.

:/

---

### Post by chris_n00b on 2007-07-26
Anyone else know what to do?

---

### Post by Immolatus on 2007-07-26
Is this a pcmcia card? If it is it might be causing a "udev" hang( thus stalling your boot process).
Try pulling out the card and boot, then edit the file in gedit (assuming you're using gnome).
Then you should be able to just plug it in and go, or plug it in and reboot and go. just a suggestion.:confused:

---

### Post by chris_n00b on 2007-07-26
Ok, yeah i pulled the card out and now it boots up fine. I will try to reedit the file then try to get internet working. I should have tried that in the first place, but I was sure that it wasn't the problem since after installing teh card it had worked fine. It was just after changing that file that it didn't boot up.

---

