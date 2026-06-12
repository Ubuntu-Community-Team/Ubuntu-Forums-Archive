---
title: "Shockwave &amp; Java &amp; Flash"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-07-15
How do i get the Shockwave Flash Palyer & JAva for Ubuntu?

Please none of the Sudu business, just quick answers.

---

### Post by Captain Kirk76 on 2006-07-15
Bump!

---

### Post by [S|G] on 2006-07-15
First, there is no shockwave player for linux.
Flash: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
Java: [http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by jimmygoon on 2006-07-15
I'm imagining you were referring to sudo? If so then that is how you execute things as the super user... as in "**s**uper **u**ser **do**"

Anyways, you will find this useful: [http://ubuntuguide.org](http://ubuntuguide.org)

In particular:
* [http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)
* [http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

There is no shockwave player for Linux. Complain to these guys: [http://www.adobe.com](http://www.adobe.com).

Good luck



edit!!!!! NOOOOOOOOOOOO!!!!!!!!!!1 Barely beaten :evil:

---

### Post by aysiu on 2006-07-15
None of the *sudo* business? How about Mepis 6, then? It's based on Ubuntu and includes Java and Flash.

As [S|G] said, though, there is no Shockwave for Linux.

If you have [extra repositories enabled](http://www.psychocats.net/ubuntu/sources), you can install both Flash and Java through Synaptic Package Manager.

---

### Post by Captain Kirk76 on 2006-07-15
Well how exactly do i get Shockwave things to work on Ubuntu.

I think i have extra repositories enables, do i will go look for Flash & Java

---

### Post by aysiu on 2006-07-15
> **Captain Kirk76 said:**
> Well how exactly do i get Shockwave things to work on Ubuntu. This works for Flash 8--I'm not sure if it'll work for Shockwave--but you can try installing the Windows version of Firefox using Wine and then install Shockwave from there.

---

### Post by Captain Kirk76 on 2006-07-15
This is originally a Windows System im using, but my XP Installation has broke, so im temp using Ubuntu Linux (which im not impressed with)

I will try searching for my XP version of FireFox * if of course Ubuntu will play nicely and Interface with the NTFS format.

---

### Post by aysiu on 2006-07-15
No, you wouldn't be using Firefox that's installed on Windows.

You would install the Windows version of Firefox on Ubuntu using a helper program called Wine.

1. Enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Install Wine ```
sudo aptitude update
sudo aptitude install wine
```

3. Download the Windows version of Firefox.

4. Right-click it and select to open it with Wine (or the command ```
wine
```)

5. Install it to somewhere in your /home folder (/home/captainkirk/firefox, for example).

6. Then go to /home/captainkirk/firefox and launch the Firefox.exe file with Wine, just as you did with the setup file before.

7. Visit a site that needs Shockwave and install it.

---

### Post by Kilz on 2006-07-15
> **Captain Kirk76 said:**
> This is originally a Windows System im using, but my XP Installation has broke, so im temp using Ubuntu Linux (which im not impressed with)

I will try searching for my XP version of FireFox * if of course Ubuntu will play nicely and Interface with the NTFS format.

Isnt it a shame there is no windows live cd and no config files to edit to fix the problem s XP gets?

---

### Post by Captain Kirk76 on 2006-07-15
For some reason, when i drag and drop things from my NTFS (XP)partiton to my ext3 (Linux) Partition, i can only put it on my desktop, never straight onto the hardrive?

---

### Post by aysiu on 2006-07-15
How is your NTFS partition mounted?

What happens when you try to put it somewhere else, like /home/captainkirk?

---

### Post by Captain Kirk76 on 2006-07-15
I cant copy, or drag and drop any file off my NTFS partition, to any location on the ext3 partition, nor can i create a new directory on the ext3 partition ( new directory is not higlighted in menu) However, if i installed a codec to XP, so it would interface with ext3, but when i copied something over from that Ubuntu had a hissy fit and deleted it next time Ubuntu was ran.??

---

### Post by aysiu on 2006-07-15
So you're trying to drag and drop within Windows to the Ext3 partition using something like this? [http://www.fs-driver.org](http://www.fs-driver.org)

Or are you in Ubuntu and dragging and dropping from a mounted Windows partition? If so, does your /etc/fstab have a line that looks something like this? ```
/dev/hda1 /media/hda1 ntfs defaults 0 0
``` or, better yet, something like this? ```
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
```

---

### Post by Captain Kirk76 on 2006-07-15
Either way dsoesnt work, If i do it XP -----> Ubuntu, Ubuntu throws a fit next time it loads, and deletes the files.

And if i try Ubuntu <---- XP It wont let me copy it to ANYWHERE on the filesystem, except the desktop, nor can i create new directory's.

And im afraid i dont understand what you mean with the code :confused:

---

### Post by [S|G] on 2006-07-15
He meant that you should edit your /etc/fstab and place that code. You can do that this way:
```
sudo nano /etc/fstab
```

Then copy and paste the contents here (if you're not confortable using nano, you can use another editor, such as gedit or kwrite, in its place)

---

### Post by aysiu on 2006-07-15
So are you using FS-driver?

For the Ubuntu side of things, try following these instructions. Post back any questions you have:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

This will mount NTFS as read-only for all users (as opposed to read-only for root).

---

