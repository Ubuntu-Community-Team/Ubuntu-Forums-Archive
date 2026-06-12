---
title: "Can't work out how to get an internet connection"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by schmidtp on 2006-04-15
G'day guys,

I've just installed ubuntu 5.10, worked pretty well. However I can't figure out how to make an internet connection with it? I've searched documentation and the forum but couldn't come up with anything.

Anyways, I'm running linux on a 1GHz athalon machine, 256M RAM, the modem is a netcomm internal modem (comes up as lucent in device manager). In the device manager it says it's there. 
Yes the modem works in windoz, that's what I'm using at the moment.
When I went through the help in unbuntu, it said to go to admin, network and connection. When I active the modem it says not working, I went to the other tab which has the dev/modem, and selected dev/ss???1 (sorry can't remember the exact phase it had), and then selected activate and it said the modem was active. I added all the internet providers info, phone number user ID etc.

Could someone point me in the right direction with some documentation or a step by step guide?? It's probably very simple, just need a steer in the right direction

Many thanks

Pete

---

### Post by BjornHaland on 2006-04-15
Hi Pete,

First of all, try and test your choices in the Networks Manager tab a little bit.

For example, I use a Wireless LAN (wlan). I have to check "ASCII" instead of "Hexadecimal".

Another example is to check "DHCP" instead of "Static IP Address".

Just try different approaches like that.

This site has a beautiful WIKI-style page. I did a search for 'modem' over there, and this is the index of what I found:

[https://wiki.ubuntu.com/FrontPage?action=fullsearch&context=180&value=modem&titlesearch=Titles](https://wiki.ubuntu.com/FrontPage?action=fullsearch&context=180&value=modem&titlesearch=Titles)

Hope this is of any help, sorry I couldn't be more specific. Good luck!

---

### Post by bscbrit on 2006-04-15
Hello 'Down Under' from, er, 'Up Top?'.

Try the following:

[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF)

Good Luck

---

### Post by schmidtp on 2006-04-17
Guys,

I'm still having no luck with getting this modem to work. I've looked around and found this guide
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF)
which seems to be what I'm after.
I've run scanmodem and got the info and followed the instuctions. It says I've got a lucent DSP modem and it's supported (good news).
Finally got the files and drivers I needed onto linux.
Now, while following through the instructions it says

"If compiling from source
On your way to configuring your modem drivers, you may find out that you need to compile from source (which means, typing commands beggining with sudo make). In that case, prior to compiling, do the following: Insert installation CD 

sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`        "

All well and good, but I don't have a modem connection as yet. So this ain't gonna work just yet.

Now I scan down to my section of the document:
Modems supported by the Lucent driver

It says:-
Setup steps:
    *
      In a terminal type

  $ sudo sh -c "echo lt_serial >> /etc/modules"
  $ sudo sh -c "echo lt_modem >> /etc/modules"

done this and nothing seemed to happen.

Onto the next step
#
to add them to the module autoloading list.
#
Since udev rewrites /dev on each boot, and some dialup programs rely on the existence of /dev/modem, you need to have a symlink created on boot (from /dev/ttyLTM0 to /dev/modem). To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:

  #ltmodem 
  KERNEL="ttyLTM0", SYMLINK="modem"

Tried to do this, but linux says I don't have permission to write to this folder. As it does with just about every other folder and floppy drive. I checked the permissions in under Admin/users/my login and it says I've got full permissions.

I haven't tried the rest of the document as yet. I'm making progress but gee's it's taking a while.

I did download a list of linux commands (which I haven't had to look at since I was working on telephone exchanges).
One other thing I found strange was in the file manager, when you try and click on a floppy drive it doesn't automatically mount it like the CD drive. The only way I've found to mount a floppy is in a terminal window and mount it that way, and then I can view whats on the floppy drive and copy files etc. As there another way I'm missing??

Thanks for the patience

Pete

---

