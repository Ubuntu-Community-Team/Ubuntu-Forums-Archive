---
title: "changing fonts in conky (or finding their names)?"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-12-31
I am trying to change the font of my dear conky, but it cannot find the name of *any* fonts I try and moreover I have almost no clue how to deal with fonts... I tried xfontsel, but it doesn't show a list of all fonts (such as those I got with xfonts-artwiz)... 

I would appreciate any help / suggestions / pointers

Here is my current conky screenshot: [http://ubuntuforums.org/attachment.php?attachmentid=4972&d=1136012276](http://ubuntuforums.org/attachment.php?attachmentid=4972&d=1136012276)

here is the font I'm in love right now: 
[http://ubuntuforums.org/attachment.php?attachmentid=4974&d=1136017060](http://ubuntuforums.org/attachment.php?attachmentid=4974&d=1136017060)

here is my conkyrc:
[http://ubuntuforums.org/attachment.php?attachmentid=4977&d=1136019942](http://ubuntuforums.org/attachment.php?attachmentid=4977&d=1136019942)

here is the conkyrc of the one I'm in love with ;)
[http://ubuntuforums.org/attachment.php?attachmentid=4982&d=1136032378](http://ubuntuforums.org/attachment.php?attachmentid=4982&d=1136032378)

and finally here is the link where this all starte 8-)
[http://ubuntuforums.org/showthread.php?t=110535](http://ubuntuforums.org/showthread.php?t=110535)

thanks in advance :)

---

### Post by Swab on 2005-12-31
Do you have the cleartype fonts installed?  I'm looking for them now but all the links I find are dead.

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=Swab]Do you have the cleartype fonts installed?  I'm looking for them now but all the links I find are dead.[/QUOTE]
I searched synaptic and packages.ubuntu.com and they are not there (so I don't have them :) )

Honestly, I could use other types of onts as well, but either I don't know how to tell conky which one to use, or conky just can't find them...

Here are the examples: ```
user@localsystem:~$ killall conky && conky -f Gelly
Conky: Xft not enabled
Conky: can't load font 'Gelly'
Conky: drawing to double buffer
Conky: forked to background, pid is 8942
user@localsystem:~$ killall conky && conky -f Arial
Conky: Xft not enabled
Conky: can't load font 'Arial'
Conky: drawing to double buffer
Conky: forked to background, pid is 8948

```
First is from xfonts-artwiz package and the second from msttcorefonts package... I'm pretty sure I'm doing something very stupid, but what?

---

### Post by Swab on 2005-12-31
[QUOTE=towsonu2003]I searched synaptic and packages.ubuntu.com and they are not there (so I don't have them :) )

Honestly, I could use other types of onts as well, but either I don't know how to tell conky which one to use, or conky just can't find them...

Here are the examples: ```
user@localsystem:~$ killall conky && conky -f Gelly
Conky: Xft not enabled
Conky: can't load font 'Gelly'
Conky: drawing to double buffer
Conky: forked to background, pid is 8942
user@localsystem:~$ killall conky && conky -f Arial
Conky: Xft not enabled
Conky: can't load font 'Arial'
Conky: drawing to double buffer
Conky: forked to background, pid is 8948

```
First is from xfonts-artwiz package and the second from msttcorefonts package... I'm pretty sure I'm doing something very stupid, but what?[/QUOTE]

I'm having the same problem.. perhaps the conky from the repositories was compiled without Xft?

---

### Post by Swab on 2005-12-31
So yeah.. im gonna try conky from conky.sourceforge.net.. will let you know... also there is an IRC channel #conky on irc.freenode.net

---

### Post by limit223 on 2005-12-31
It seems that your xft and xfstt services are not loaded....I'm in Kde ...try find  out in gnome if there are on..

---

### Post by Swab on 2005-12-31
So I installed conky_1.3.3-1_i386.deb from conky website.. and now I can specify any font I like!

---

### Post by limit223 on 2005-12-31
I really didn't get this error...mine is compiled from source 1.3.4...but is possible the .deb from repo to be compiled without xft...

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=Swab]So I installed conky_1.3.3-1_i386.deb from conky website.. and now I can specify any font I like![/QUOTE]
hmm okay then let me try it from the conky site as well... as for the xft and xfstt services -> no clue and google doesn't have anything on them either... let me see what happens with the one from conky site...

---

### Post by xtacocorex on 2005-12-31
I just built a package from the source and tried the .conkyrc that you want to use and I get the font change, but I get this wierd flash effect with it, but that's another problem on my end, probably due to my crappy graphics card.

I think you need to enable xfs if it isn't started on boot.

The script in this thread: [http://ubuntuforums.org/showthread.php?t=20583](http://ubuntuforums.org/showthread.php?t=20583) is similiar to the SGI and RedHat chkconfig program that manages services, keeps from messing with the update.rc stuff by hand. 

Or I guess if you have BUM, you could start xfs from there.

---

### Post by towsonu2003 on 2005-12-31
great help everyone. I'm scared that I got so much help ;) so nice community. 

the flash effect ou mention with my conkyrc, I remember, is due to the ip numbers displayed...

while installing 1.3.3 deb, I got this error but it still runs (as 1.3.) so it should be okay although the CPU usage of xorg went up to 50% ```
sudo dpkg -i packages/conky/conky_1.3.3-1_i386.deb
(Reading database ... 131040 files and directories currently installed.)
Unpacking conky (from .../conky/conky_1.3.3-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing packages/conky/conky_1.3.3-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/conky/AUTHORS')
Errors were encountered while processing:
 packages/conky/conky_1.3.3-1_i386.deb

```

let me try other fonts and if not good, will go back to ubuntu's conky I guess

---

### Post by towsonu2003 on 2005-12-31
nope
all fonts (xft enabled) make xorg use cpu like there is no tomorrow. I guess my hardware (ATI) is not good for this....
?
:(
maybe that's why ubuntu pple did not compile this with xft enabled?

well, I should memorize this: "don't fix it if it ain't broken"...

---

### Post by xtacocorex on 2005-12-31
Did you have another version of conky installed before installing the new package? I got a similiar error when building mine because I forgot to remove the one from the repos.

My .conkyrc file doesn't show my ip and it still flickers, but I'm not too worried about it.  I might modify mine some more and get rid of the temp monitor as I know the kicker applet that I had at one point to monitor temp had a similar effect.

---

### Post by limit223 on 2005-12-31
For flickering take a look here:
[http://www.ubuntuforums.org/showpost.php?p=579902&postcount=90](http://www.ubuntuforums.org/showpost.php?p=579902&postcount=90)

towsonu2003,
I've got an ATI card as well ...xft works great on mine...and conky as well..all you need to do just remove old conky from .deb..and compile the new ver from source... 
Extras from README:
"........................
COMPILING
       For  users  compiling from source, make sure you have the X development
       libraries installed.  This should be  a	package	 along	the  lines  of
       "libx11-dev or xorg-x11-dev".

       Gentoo users -- Conky is in Gentoo's Portage... simply use "emerge app-
       admin/conky" for installation.  There is	 also  usually	an  up-to-date
       ebuild within Conky's package or in CVS.

       Debian,etc.  users  --  Conky will be in Debian's repositories soon (by
       mid-September, hopefully), and then Ubuntu  shortly  thereafter.	 Until
       then, "dpkg -i" the .deb package to install.

       Example	to  compile  and  run Conky with all optional components (note
       that some configure options may differ for your system):

       sh autogen.sh # Only required if building from CVS

       ./configure  --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft  --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime  --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon

       make

       make install
................................"


PS. Happy New Year!!!

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=xtacocorex]Did you have another version of conky installed before installing the new package? [/QUOTE]
I did (1.3.1 from repos) but I purged it bf installing the new one...

limit223-> hey thanks for the compiling info :) I'll try that (next year ;) ) happy new year to you too (and to all)!

---

### Post by xtacocorex on 2005-12-31
[QUOTE=limit223]For flickering take a look here:
[http://www.ubuntuforums.org/showpost.php?p=579902&postcount=90](http://www.ubuntuforums.org/showpost.php?p=579902&postcount=90)
[/QUOTE]

That worked perfectly, now I can actually use it.

towsonu2003:
What type of ATI card do you have? My Dell has a Mobility Radeon M6 (32Mb) and I don't seem to have a problem with xorg usage. I have no clue what other help I can give, but I'm assuming that your graphics card is better than mine.

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=xtacocorex]
towsonu2003:
I have no clue what other help I can give, but I'm assuming that your graphics card is better than mine.[/QUOTE]

that's okay dn't worry :) no need for further help so far :cool:  thanks so much though. this community keeps surprising me ;)

In the meantime, just FYI, I have an ATI Mobility Radeon 9000 IGP (I think it's 126MB shared memory?) on a hp pavilion zv5120us laptop. 

lspci (if that's where I'm supposed to look at :) ) reports everything ATI related as unknown device while xorg.conf says it's a ```
 Identifier      "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
Device          "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"

``` and the driver it uses is "ati". Let me attach the xorg.conf, but I don't expect any help (long file, hard to help with such issues etc and the problem is so far minor <- conky) :D 

I believe the problem is not the hardware itself, but the drivers used in linux (as usual in my case ;) ) for this machine...

I once tried to use the proprietary drivers but they broke everything so I am in a "dont fix it if it ain't broken" mode with my 'dear' ati card... I think I'll try them again when dapper comes in. games (3d) are in my windows partition so that's okay. 

With my xorg cpu usage going off, I am guessing using xft hits hard my not-working-properly drivers at home ;)

---

### Post by limit223 on 2005-12-31
If I don't mistaken your cards fall in  the ATI RADEON 8500 series and higher cathegory which has all support with fglrx driver....this is the guide to install it:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
A new version of it is up ..check with ati.com:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

My card is Radeon Sapphire X600 PCI 128MB.

towsonu2003,
take a look here: your card is supported by this driver:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.20.8.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.20.8.html)

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=limit223]If I don't mistaken your cards fall in  the ATI RADEON 8500 series and higher cathegory which has all support with fglrx driver....this is the guide to install it:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
A new version of it is up ..check with ati.com:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

My card is Radeon Sapphire X600 PCI 128MB.

towsonu2003,
take a look here: your card is supported by this driver:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.20.8.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.20.8.html)[/QUOTE]
thanks a lot. let me give it a try and see. :cool: I really appreciate the help.

---

### Post by limit223 on 2005-12-31
Anytime..you are welcome!:)

---

