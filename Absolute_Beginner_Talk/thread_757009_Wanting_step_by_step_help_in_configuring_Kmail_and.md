---
title: "Wanting step by step help in configuring Kmail and printer."
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by sashag on 2008-04-16
Hi Everyone!

This is my first post here! I'm mainly using Windows XP right now, although I also have Linux Kubuntu installed at the same time. I have a few questions that I hope I can get answered in this forum.

First question: How do I make Windows XP as my 'default' OS? I need step by step assistance that I can print out.

Second question: I still need help in setting up Kmail properly.  I keep getting the message 'no host localhost' whenever I try to send or recieve
e-mails. I got all the info from my local telephone company on the e-mail
setup, but I can't get the setup configured properly using Kubuntu. I need step by step help in this area as well.

Final question: I want to set up my printer (a Lexmark Z55) so that it can
run using the Kubuntu OS. I need step by step help with this as well.

I'm hoping that someone who use Linux Kubuntu on a regular basis can give me step by instructions together in one post so that I don't have to go hunting for the steps in different posts and so that I can print out the instructions as one.

Thank you very much to those of you who want to take the time to do this as I can't use Kubuntu if I don't have the basics set up. The 'sparse'
manual that came with the 'live' download hasn't been of any help at
all as it seems that the Kubuntu OS already assumes that you know what you are doing since I have downloaded the OS in the first place!
Anyway, thanks all!

---

### Post by Meskarune on 2008-04-16
To make window's default do this in the konsole:

```
sudo kate /boot/grub/menu.lst 
```

Put in your password and then kate will open the menu.list 

Go to the part where it looks like this: 

```
title		Kubuntu Feisty Fawn 7.04
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2a71bfd7-67bf-40ec-b5ed-1f1ebd0b0faa ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Change "savedefault" to default 0

Then scroll down a little and under the window's heading change "default 0" to "savedefault"

After that save the text file. Grub should now load windows first.

---

### Post by Meskarune on 2008-04-16
> **sashag said:**
> 

Second question: I still need help in setting up Kmail properly.  I keep getting the message 'no host localhost' whenever I try to send or recieve
e-mails. I got all the info from my local telephone company on the e-mail
setup, but I can't get the setup configured properly using Kubuntu. I need step by step help in this area as well.



I would need more information to answer that correctly. What e-mail service do you use? What is the information they gave to you? (excluding your password of course)

---

### Post by Meskarune on 2008-04-16
1. Open a terminal (Applications > Accessories > Terminal) and follow these steps

2. Make sure you have installed the following packages
```

sudo apt-get install libstdc++5 alien
```

3. You have to download the Lexmark driver from [WWW] [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)
```

mkdir lexmark
cd lexmark
wget http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz
```

4. Then you have to extract the content
```

tar xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```

5. You now have a lot of files in your current directory, the driver is buried inside a shell-script, and you have to dig it out:
```

tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
```

6. Unpack your new tar-archive:

```
tar xvzf install.tar.gz
```

7. Unfortunately Lexmark has only given you .rpm-packages, and you have to extract the content of those:
```

alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm
```

8. Now you have to extract the newly made tgz-files which contains the drivers, and copy them to their locations. !!! Important: do exactly as written, otherwise your system may become ruined !!!
```

tar xvzf z600llpddk-2.0.tgz
tar xvzf z600cups-1.0.tgz
cd usr
sudo cp -a * /usr
sudo ldconfig # Reloading library-database
```

9. The drivers are now installed and copied to their locations. Test everything out with the following command:
```

/usr/lib/cups/backend/z600
```

10. If the output is something similar to this:
```

direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"
```

Then it is working.

11. Reload CUPS:

```
sudo /etc/init.d/cupsys restart
```

12. Make sure your printer is plugged in and go to System > Administration > Printing and double click New Printer. In the first screen, select your printer and click Forward. In the second screen, click Install Driver and navigate to /usr/share/cups/model/ then double click Lexmark-Z600-lxz600cj-cups.ppd.gz. Click Forward twice and your printer should be installed. If your printer does not show up, repeat this step. 

These instructions are from: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

---

### Post by Meskarune on 2008-04-16
PS: You really should take the time to search out and find this information yourself. That's why the online ubuntu documentation is there. All you would have to do to make a "printable"verions is copy/paste the information into a document. And it really isn't nessesary to do that. Just have your browser open on the page and follow the instructions. You have a lot of things to learn, and you can't come ask questions in the forum everytime something well documented and minor comes up. Most people wouldn't bother to answer. the fastest way to learn how to use Kubuntu is by reading the docs. Thats what they are there for. There are plenty of tutorials. Using linux is not as scary as it looks.

---

