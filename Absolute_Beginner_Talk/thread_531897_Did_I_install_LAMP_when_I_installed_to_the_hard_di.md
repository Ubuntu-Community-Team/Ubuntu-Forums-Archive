---
title: "Did I install LAMP when I installed to the hard disk?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by GA_M on 2007-08-22
Hi!

My first post!!

I have a question:  I don't know what I was thinking, but I installed Ubuntu Server 6.06 by selecting "Install to the hard disk" instead of "Install a LAMP server".

However,* I do want a LAMP server* installed to the hard disk.

Did LAMP get installed or do I need to install Apache, MySQL and php separately now?

-----

Another question, if I may: the first time I installed it, there was an error while installing the base system. When I tried to re-install it, I selected to partition it by erasing the entire disk (as before) but this time *using LVM*... and it worked.  Is that OK?  (It's a small hard drive, under 10 GB.)  I looked at the Wikipedia definition of LVM and didn't understand a thing...

THANK YOU SO MUCH!

John

If you are also willing to help with my issue below, well... that'd be wonderful.

P.S. I'm_ trying_ to learn Ubuntu Server -- it's exciting! Webmin is my next step...* if* I can figure out how to install it from a .deb file that I downloaded onto my Windows XP.  I tried burning it as an image file (using InfraRecorder) but got an error message.  Any ideas?  Thanks again.

:confused:

---

### Post by renzokuken on 2007-08-22
firstly, installing a Server edition should have installed LAMP, i recently did a server install and have LAMP.

secondly, copy the .deb file over to your ubuntu machine and place it in your home folder. open up a terminal and run

```
sudo dpkg -i webmin_version.deb
```

(obviously replacing "webmin_version" with the actual filename

---

### Post by TheOrangePeanut on 2007-08-22
I don't know about 6.06, but in Feisty I installed server but didn't get LAMP.  There were only two choices during installation, LAMP and DNS, and I chose the correct choice, but LAMP wasn't installed.  I had to install apache, mysql, and php separately.  Weird.

This post is no help really, just commentary :popcorn:

---

### Post by hyper_ch on 2007-08-22
For setting up a server I'd follow this here:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by eentonig on 2007-08-22
To install LAMP server

> sudo tasksel

And then select the options you want.

---

### Post by eentonig on 2007-08-22
And why do you want to install from a downloaded .deb? Use the one in your repo's

> user@host:/var/www/new$ apt-cache search webmin
webmin - A web-based administration interface for Unix systems.
user@host:/var/www/new$ sudo apt-get install webmin

---

### Post by GA_M on 2007-08-23
Hello.

Thank you so much for your help.

Hyper-CH, I went to the [website you recommended]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3") and was able to do everything up to and including Step 4, *Installing the SSH Server*.  

However, I am now stuck at Step 5: I did type *vi /etc/network/interfaces* and then entered the address, netmask, network, broadcast and gateway IPs, but now I don't know what to do. I entered the following commands, as the website tutorial states: "*/etc/init.d/networking restart*" but I'm just adding to the list of addresses.  So I deleted that (leaving the addresses) and finally after trying everything, ALT/TAB worked for me: I then entered /.  As soon as I do that it takes me at the bottom of the screen.

That's when I entered */etc/init.d/networking restart* and pressed Enter.  That's when I get a warning: "**E486: Pattern not found: etc**"

So, I'm stuck there. The author of the[ website]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3") states that that's how to restart the network, but it doesn't work for me -- I must be doing something wrong.  PLEASE HELP ME!  Thanks!    ](*,)
--------------------------------------------------

Renzokuken, thanks for your help. What you say makes sense, except that I am much less knowledgeable than you think, as I have no idea how to "copy the .deb file over to the ubuntu machine and place it in the home folder".  The XP and the Ubuntu Server share the same router, that's about all I know: I still don't know how to move one file from one computer to the other, and there is no cable linking the two directly. I did do the Network Setup Wizard on Windows XP, but at the end I was told that for it to work the wizard needs to be run on each computer -- how am I supposed to do that, if the other computer is the Ubuntu Server?!  I may decide to install the Xubuntu GUI to facilitate that, and then once it's properly set up, uninstall it and return to the regular Ubuntu Server (hoping that the changes/settings aren't forgotten). [Also, I was told that the workgroup names must match: how do I find out what the workgroup name under Ubuntu Server is?]
--------------------------------------------------------

Orange Peanut, thank you.  How did you know that LAMP had [U]not[U] been installed when you installed Feisty Fawn?
---------------------------------------------------------

Eentonig, lovely picture -- your child?
Thank you for your help  :)  I wanted to install it from the downloaded .deb because I read somewhere else that that's the best way to guarantee that one has the most recent, up-to-date software.

> user@host:/var/www/new$ apt-cache search webmin
webmin - A web-based administration interface for Unix systems.
user@host:/var/www/new$ sudo apt-get install webmin

Eentonig, do I just type the first and third line?  THANKS
-----------------

I did try different ways, but I'm embarassed to admit I don't fully remember what else I attempted...

Hope you're able and willing to help this dazed and confused Linux user!  The whole thing is almost consuming me -- I just want to get it up and running!  :shock: :frown: [-o<

So if I *temporarily* give up and install a GUI like Ubuntu Desktop or Xubuntu, will the computer remember my networking/computer settings once I revert back to the server (GUI-free) version?

T H A N K S !!

---

### Post by Wim Sturkenboom on 2007-08-23
You're not supposed to type that '/etc/init.d/networking restart' in vi ;) The '/' that takes you to the bottom of the screen is the start of the search function in vi.

First save your work (press <esc>, press the colon and type wq followed by <enter>) and at the command line type the command.

---

### Post by GA_M on 2007-08-23
THANK YOU!!  :)

Now I need to call the DSL company to help me out: I assigned the same IP to both computers, and there's a conflict...  :rolleyes:    I _knew_ that there would be more problems!

But again, THANK YOU so much.

---

### Post by Wim Sturkenboom on 2007-08-24
Are you connecting two computers to the internet? In that case you need a hardware router or setup on PC as a router. The router will receive the IP address from the DSL provider (DHCP) or have a fixed IP address (if your provider gives you that) and redistribute requests to the other PCs.

---

### Post by hyper_ch on 2007-08-24
Well, "vi" is a very powerfull command line editor (however I think it's too complicated for me). I perfer "nano". You can edit files just like this:

```

nano file

```

In nano you can use the arrow and page up/down keys to navigate around. With  ctrl-w you can search for a string.
With ctrl-x you exit nano - if you have modified the file you will be asked if you want to save it (and if you do, where you want to save it to or whether you want to overwrite it).

Regarding the IPs:
On my cable modem I can retireve up to 4 IPs. On DSL I think you only have one -> so if you want to hookup multiple computers to the internet but have only one IP you need some kind of a router.

If you don't have a static/fixed IP you probably also want to make use of some dynamic service like dyndns.com or no-ip.com.

---

