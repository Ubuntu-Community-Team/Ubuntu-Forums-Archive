---
title: "X Server Help"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by swivelgames on 2006-04-02
Hey, I am getting an X Server problem because its not configured or setup or installed or something like that, and was woundering if any could help. I have done alot, and when I first installed linux I got this problem, so I decided to try doing it another time. So I uninstalled Linux and got some GRUB 22 error. So reinstalled Ubuntu and got the same X Server error, I would like to just use Ubuntu like I use windows, NORMALY!

---

### Post by Ramses de Norre on 2006-04-02
I guess you get a terminal when you boot ubuntu? Do
```
sudo dpkg-reconfigure xserver-xorg
```in there to configure X, if that's the problem.

---

### Post by swivelgames on 2006-04-02
When I get into the Ubuntu command line?

---

### Post by Mark_in_Hollywood on 2006-04-02
Terminal from Applicataions / System, I think.

But: See my post X gui gone bye bye. It near yours, at least for a couple of hours this Sunday 2.4.06

---

### Post by catlett on 2006-04-02
What happens when you start your computer. Does it say Grub loading stage 1.5...... ? Do you get the Grub menu where you can choose which OS to boot from(Ubuntu kernel 2.6.10 or Windows XP)? If that happens, what happens when you try to boot to Ubuntu? Do you get a login screen? It will look similar to windows login screen. You have to ype your name and password. Or do you get a command line? Something like swivelgames@computer:-1 with a flashing cursor. Or does nothing happen and your computer doesn't boot when you pick Ubuntu? Once we know what the process is someone can give you the command or the process to get Ubuntu up.

---

### Post by swivelgames on 2006-04-02
I Turn on my comp, it loads Grub Stage 1.5, I choose Ubuntu, it goes to the loading screen, looks normal. I get a black screen and then it tells me in a DOS type way that my X Server is not configured or installed properly or something, I click ok and it goes to a command screen asking me for my username and password, and I am using ubuntu in command not GUI based. I need help on getting the X Server to work and I have no idea what you guys are talking about. I am a n00b to ubuntu I need baby step by steps please, just something that I can do easily. I am a programmer so I am not that stupid but I do need some help I have never used any type of Linux before.

---

### Post by Mark_in_Hollywood on 2006-04-02
At boot time, press the Escape key, once.

The screen will show

Ubuntu
Recover mode
Memory test

or something similar.

Use the cursor key to select recovery mode and press enter (oopss I forgot this a few moments ago)

when prompted give your username and password and press enter

when you see something like

username@something#:

type

sudo dpkg -reconfigure xserver-xorg

press return

answer any questions as best you can.

I've been at this about 10 days now and have been using Ubuntu for about a month.

---

### Post by swivelgames on 2006-04-02
Ok, thanks, now do you want me to go into the recovery console or just let it load ubuntu and use the command line console? The way you discribed it to be they sounded the same.

---

### Post by hbinded on 2006-04-02
I also have the same problem. I tried all the advice given, but I still get the same problem. What can I do now? still haven't got to see the awesome desktop of Ubuntu!](*,)

---

### Post by catlett on 2006-04-02
If you can get into Ubuntu and you can open the terminal then follow the origional advice from Ramses de Norre
> I guess you get a terminal when you boot ubuntu? Do
```
sudo dpkg-reconfigure xserver-xorg
```
 to configure X, if that's the problem.




Applications<Accessories<Terminal

---

### Post by catlett on 2006-04-02
> I also have the same problem. I tried all the advice given, but I still get the same problem. What can I do now? still haven't got to see the awesome desktop of Ubuntu!
Post seperately and explain what is happening. I.E can you boot at all, do you get a log in screen, do you get a command line? People here can help but tyhey need to know what's going on on your end. Regards.

---

### Post by hbinded on 2006-04-02
I already did that. A kind of wizard came up and I was asked some questions about my video card (which is an ATI X700 SE with 256 MB PCI-e) and it was detected correctly. I then selected the correct resolution for my monitor and restarted my computer after going through some more config. (mouse, keyboard...). But I still dont get a gui.

---

### Post by catlett on 2006-04-02
What do you get? A command line? 
Go to the absolute beginners forum and click on "start a new thread". Use as a title "Can't get gui, stuck on command line". For the meat of the post write" I can't get into the gnome desktop. I am stuck at the command line. I tried sudo dpkg-reconfigure xserver-xorg . When I did that  a kind of wizard came up and I was asked some questions about my video card (which is an ATI X700 SE with 256 MB PCI-e) and it was detected correctly. I then selected the correct resolution for my monitor and restarted my computer after going through some more config. (mouse, keyboard...). But I still dont get a gui. Can anyone help?" 
Someone will know the correct comands to enter but you have to get off this thread. To get your problem noticed.

---

### Post by hbinded on 2006-04-02
now that's where the problem is: I can't get into ubuntu. It just load's me into a command-like shell. No gui at all. Tried the advice, but I still don't have a gui.

---

### Post by catlett on 2006-04-02
Did you try the startx command. I haven't had this problem with Ubuntu but on my other computer I have Debian and I put Gnome on but all I got was a coimmand line. I had to type startx .I guess with Ubuntu it would be sudo startx. Your problem might be the gnome desktop. Try sudo apt-get install gdm.It would be best to post your own thread. If you can post here you can post your own. This way more people will see it and you'll find someone smarter than me.

---

### Post by Mark_in_Hollywood on 2006-04-03
I have the exact same problem. I have tried "startx" and "sudo /etc/init.d/gdm restart".

Neither of the foregoing commands returns me to the gnome desktop or gui.

In /var/log/Xorg.0.log

I see:

Fatal Server Error
No valid FontPath could be found.

I looked in /etc/X11/xorg.conf

the lines in there do contain a FontPath statement, but according to the Breezy Upgrade Notes ([https://wiki.ubuntu.com/BreezyUpgradeNotes)](https://wiki.ubuntu.com/BreezyUpgradeNotes)).  I have the correct lines in that config file.

I even changed the /var/lib/X11/defoma . . .

to

/usr/share/X11/defoma . . .

After all this, I think it would be easiest to get on-line and using apt-get do 

apt-get install --reinstall xserver-xorg

but to do that, I need to know how to get wvdial to call apt-get or vice-versa. I'm newbie enough to have tried and failed at this.

PLEASE, someone with the know-how let me know how.

Thanks.

---

