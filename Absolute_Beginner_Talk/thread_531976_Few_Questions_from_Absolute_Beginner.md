---
title: "Few Questions from Absolute Beginner"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by blinkja on 2007-08-22
Hello,

1.how do i install that file ends in .tar.gz i have downloaded firefox and winrar to desktop ( please can i get in detail installtion as i am absolute beginner).
2.I have downloaded a few video files what program do i use to play these files?
and is there a version like K lite mega codec pack for linux to play popular video/audio formats?
3.How to view clear type of webpages like windows xp?

---

### Post by Dark Star on 2007-08-22
To install .tar.gz file unzip it and place the folder in /home/<user name>
Then open terminal and do this 
```

./configure
make
sudo make install
```

Note: You must have a C++ compiler installed in your OS for that :)

2. Install Gstreamer Media Codec from Add or remove :)
3. Didn't get your ques ?:S

---

### Post by overdrank on 2007-08-22
> **blinkja said:**
> Hello,

1.how do i install that file ends in .tar.gz i have downloaded firefox and winrar to desktop ( please can i get in detail installtion as i am absolute beginner).
2.I have downloaded a few video files what program do i use to play these files?
and is there a version like K lite mega codec pack for linux to play popular video/audio formats?
3.How to view clear type of webpages like windows xp?

Hi and welcome for the installation 
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
For video you will need the codecs and restricted formats and for a player you can search synaptic manager or add and remove
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Hope this helps and good luck!

---

### Post by Canuckelhead on 2007-08-22
for question #2
you can use automatix to help out with the video...  [http://http://www.getautomatix.com/]("http://http://www.getautomatix.com/")  be careful because regional laws apply to codecs...
I also don't understand question #3

---

### Post by nvteighen on 2007-08-22
Just a question, why have you downloaded Firefox from a .tar.gz? You can do it by Applications --> Add/Remove. There, you search "firefox", check it and click OK.

But, for any other case, to install a .tar.gz, you'll need to do this before.

1. Go to Applications --> Accessories --> Terminal
2. Type:
```

sudo apt-get update && sudo apt-get install build-essential

```

The "build-essential" package will make you able to do what Dark Star told you. (weirdly, Ubuntu doesn't install it by default, when other Linux distros do)

---

### Post by hyper_ch on 2007-08-22
It is not adviced to use automatix.

---

### Post by nvteighen on 2007-08-22
I understand Question 3.

Well, I think you won't be able, because Microsoft ClearType is only for Internet Explorer 7. Neither Firefox in Windows can use it nor even IE 6! 

For those who don't understood what ClearType is: it's a tool that renders fonts with smooth edges and is meant to make webpages more readable... I personally hated it and was my reason 2 to switch into Firefox.

---

### Post by philinux on 2007-08-22
As far as firefox goes its already installed with ubunty feisty. However if you want the mozilla version that updates on a regular basis then use ubuntuzilla. I've got firefox and thunderbird installed this way. It leaves the original install untouched so that it does not bugger up synaptic manager.

[http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net)

All the instructions are there too.

---

### Post by Dark Star on 2007-08-22
> **nvteighen said:**
> I understand Question 3.

Well, I think you won't be able, because Microsoft ClearType is only for Internet Explorer 7. Neither Firefox in Windows can use it nor even IE 6! 

For those who don't understood what ClearType is: it's a tool that renders fonts with smooth edges and is meant to make webpages more readable... I personally hated it and was my reason 2 to switch into Firefox.
Thanks for the info :) :p

---

### Post by blinkja on 2007-08-22
thanks

I could not get winrar to install when type i get this 

> me@me-desktop:~$ ./configure make sudo make install
bash: ./configure: No such file or directory
me@me-desktop:~$ 

i extracted rarlinux-3.7.0.tar.gz to desktop it created **rar** folder now what i do? :confused:

---

### Post by blinkja on 2007-08-22
Ok i searched for rar in add remove programs and installed rar by Eugene Roshal 

i never know there are many software in add/remove panel :)

now i can extract rar files!!

thanks

---

### Post by Terl on 2007-08-22
You know you can get the rar plugins via synaptic right?  Have you looked at the programs available to you to add/remove packages?

EDIT:  I see you already got that!  There are thousands of programs available to you via apt/synaptic.  Have fun!

---

### Post by blinkja on 2007-08-22
hey and thanks,
I dunno what is good software as i am new to ubuntu. 
and these type of software are regular in this computer when running windows OS.
for a beginner what do you recommend for torrents, download manager, DVD player?

---

### Post by nvteighen on 2007-08-22
> **blinkja said:**
> Ok i searched for rar in add remove programs and installed rar by Eugene Roshal 

i never know there are many software in add/remove panel :)

now i can extract rar files!!

thanks

That's one difference between Linux and Windows. In Linux, when you need a software, you generally use applications called "Package Managers" (Add/Remove, for example, but there are another three installed and all use the same database)... Actually, you should very rarely download things directly from webpages, mainly because it is harder and also it can turn into a security risk.

---

### Post by hyper_ch on 2007-08-22
Download Manager:  d4x
Media Player: vlc
Torrent: Hmmm....   azureus, ktorrent, deluge    or I prefer now command line clients like rtorrent...   quite some people run   utorrent  through wine.

---

### Post by 3rdalbum on 2007-08-22
Since you mention DVD players, you should be aware that DVDs are encrypted and the decryption key is controlled by media companies. These companies only give out the decryption key to people who pay them A Lot Of Money. Obviously, since Ubuntu and Ubuntu's software are free, they do not come with a decryption key.

There is a method of decryption that does not require the licensed decryption key, and that is through a package called "libdvdcss2". As it decrypts digital media, it may be illegal in your country. You can get a copy of libdvdcss2 from Medibuntu - [www.medibuntu.org](www.medibuntu.org) will show you how to get this vital library. You will also need the packages:

libdvdnav4
libdvdplay0
libdvdread3

As well as VLC (which is a good DVD player).

**Please check the laws of your country and state (if applicable) to see if unlicensed media decryption is illegal, before installing the libdvdcss2 library.**

---

