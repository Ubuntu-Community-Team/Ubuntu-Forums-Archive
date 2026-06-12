---
title: "DVD plugin installation confusion"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by brightmatter on 2006-10-26
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart Totem to be able to play this media.

Yes, I know, there are a million people asking a million questions regarding their DVD ROMs but I am 2 days new into Ubuntu and all I ever needed was for it to access the internet, use ooffice and play DVDs.  2 out of three are good to go.  Now for the third.

Movie Player states it cannot play my DVD.  It is a normal DVD, nothing special.  I read the page regarding restricted files and it said I need some kind of codec package.  It did not however tell me the following.

1.  What is the website address for the codec package install (the link)?
2.  once downloaded, where do i put it (what folder)?
3.  Once it is in the folder, what is the command line i type to install it?

it is telling me stuff like i need to enable restricted files in system>administration>synaptic package manager>settings>repository and then select every check mark and then enter each selection and select universe and multiverse.  I do this and then close.  I reenter to check to make sure the settings worked and they are again unchecked.  I check them again and again leave.  I reopen them again to check to see if it is still checked and they are again unchecked.](*,) 

What does any of that stuff got to do with my DVD not playing and where is the codec?:confused: I am so confused, please, someone help me.:(

I found these commands that are supposed to work.  I open terminal and paste them in and press enter...... all i get is an error.  Next I try one line at a time..... again, error.

sudo apt-get install libdvdread3
E: Couldn't find package libdvdread3

sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found

---

### Post by blendmaster on 2006-10-26
[automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38")!

It couldn't get easier. Install it, and open it, and select to install w32codec packages. You need to enable extra repositories because this isn't open-source stuff, so Ubuntu won't like it if you don't (well, Synaptic won't, you should enable these anyway).

Automatix is awesome!

---

### Post by DSn0wMan on 2006-10-26
You can also try easyubuntu from freecontrib.org.

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Very easy GUI to isnstall the goodies you need.

---

### Post by Prefader on 2006-10-26
Also a good time to mention [http://ubuntuguide.org](http://ubuntuguide.org) -

Step by step instructions for tons of stuff there (including DVD playback).  :)

---

### Post by brightmatter on 2006-10-28
Sadly none of the suggestions have proven to be helpful for a Linux n00b like myself.  It has been four painful days of unintelligible command line editing and I still cannot play a simple DVD.:evil:   That is not good.  Thanks for the attempt but even the simplest things don't seem to work in Ubuntu.  Sadly, it just isn't baked enough for people like myself, (that would be people with 12 or less years of computer experience). I see no other choice.  I will be returning to Windows XP.  Wish I could say it has been fun.  I wish you all the best of luck.  Maybe It will be ready in another 5-10 years.

---

### Post by PriceChild on 2006-10-28
Dapper or Edgy?

The instructions are different...

Either way, you should have read [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) to work both out.

In Dapper:```
sudo apt-get install [B]libdvdread3
[/B]sudo  /usr/share/doc/libdvdread3/examples/install-css.sh
```
In Edgy:```
sudo apt-get install [B]libdvdread3
[/B]sudo  /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by Dual Cortex on 2006-10-28
Well... doesn't look like he's coming back. Can't believe he couldn't follow copy and paste instructions.
People like them rise others in power... reminds me of my signature.

---

### Post by jauru on 2006-11-08
I stumbled upon your instructions (PriceChild's) trying to find a resolution to my Totem DVD player problems.

I  followed your instructions (cut & paste - I'm on Edgy) and the instructions seemed to work just fine, yet I *still* get the messsage "Totem can not play this type of media (DVD) because you do not have the appropriate plugins to handle it."

So what should I do now?

---

### Post by barefootpenguin on 2007-01-29
I, also, am running Edgy, have followed the instructions (Price child's) above, and still get the same error message on Totem when trying to play a DVD. What else can I try? Why doesn't Totem come with the ability to play DVD's?  Thanks.

---

### Post by PedroDelGibbio on 2007-02-07
I too thought Price Child's advice was just the ticket but no dice.  

As an Ubuntu novice looking to get a simple media player machine, I've got Totem playing MP3 and AVI files but not DVDs yet and following the suggested install, which brought up a host of positive looking messaged in the console, it still didn't work and gave the same message.

Help would be appreciated!

---

### Post by Maestro23 on 2007-02-07
> **PedroDelGibbio said:**
> I too thought Price Child's advice was just the ticket but no dice.  

As an Ubuntu novice looking to get a simple media player machine, I've got Totem playing MP3 and AVI files but not DVDs yet and following the suggested install, which brought up a host of positive looking messaged in the console, it still didn't work and gave the same message.

Help would be appreciated!

Have you looked into maybe trying mplayer or vlc(videolan).  I use both of these and have no problems playing DVDs in either of them.  Both are available via synaptic if you have all your repositories correct and your Win32 codecs installed.  Just something for you to think about.

---

### Post by tchansen on 2007-02-07
> **barefootpenguin said:**
> Why doesn't Totem come with the ability to play DVD's? 

If I remember correctly, it has to do with licensing.  As Ubuntu is provided free of charge to any who want it they can't include code that would make it illegal in some parts of the world, especially the United States.  

When you enable the restricted libraries, you are taking the responsibility for making sure that using the code available isn't illegal where you live.  With that said, I don't know of anyone that doesn't turn on those libraries immediately.  However, it can't come that way for liability reasons for the people and organization that provides Ubuntu.

Now, that is what I remember about the issue - if I've got some of it (or all of it) incorrect I'd expect someone to correct me, hopefully with as little flames as possible.

:D

---

### Post by PedroDelGibbio on 2007-02-08
Maestro23, thanks for the advice.  That didn't really do it for me, but the link at the footer of your post put me right on track.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability)

Turns out the only thing I was missing after the post from Price Child was to then:
 sudo aptitude install totem-xine

Once I did that, DVDs play fine in Totem.

This newbie can see himself sticking with Ubuntu!

---

### Post by trents on 2007-03-02
I'm not going to address the ethics of the licensing issue but I will give some advice about how to get Totem to play DVD's. I too installed all the free and non-free codecs through Automatix and also through a similar product, Easy Ubuntu. Like the original author of this thread, that did not make Totem DVD capable for me. But here is what did work after installing all the codecs: I installed VLC with the Ubuntu Add/Remove installer app. I found that VLC would play DVD's. I also found that now Totem would too.

Steve

---

### Post by Mets on 2007-03-02
Well, if the guy can't download Automatix/EasyUbuntu and click the "Install" button next to "DVD Codecs" then he probably isn't ready for linux just yet, even Ubuntu.

That being said, Totem is not a very good media player and can be very fussy.  VLC will literally play anything, and requires no extra codecs since it has them all built in, so use that or use MPlayer if you can get your codecs together.  There's no point wasting your time trying to get Totem to work when you can download a player that will work right out of the box, and is better anyway.

---

### Post by panch0 on 2007-03-02
MPlayer plays DVDs just fine with libdvdread and libdvdcss. KPlayer is a nice frontend for KDE, not sure how well it will work on Gnome though.

---

### Post by mawdryn on 2007-03-09
I had the same problem, but running 'sudo aptitude install totem-xine' fixed it for me.

---

### Post by Horza on 2007-03-10
Does anyone know how VLC and MPlayer compare with gxine for DVD playback?  I've gotten this last one to work, but if either of these are known to be better would like to check them out (limited time for messing around).  Thanks.

ATQ:  here's somebody who finds gxine better than MPlayer for DVD playback, tho MPlayer is better for some things:

 [http://www.linuxis.us/linux/media/howto/linux-htpc/htpc_software.html](http://www.linuxis.us/linux/media/howto/linux-htpc/htpc_software.html)

I installed libdvdplay0 and libdvdnav4 along with gxine and libdvdread3, but I'm not sure that they're needed.

Also, it's not too hard to read the install script in /usr/share/doc/libdvdread3/examples, and collect the appropriate version of the libdvdcss package from the Swedish site, in case the MPAA manages to nuke it or something.  This can be put into an APTonCD repository along with all the other stuff, and reinstalled without connecting to the internet or other stuffing around.

How to stop Totem from trying to play dvds:

 Settings|Preferences|Removable drives and Media|Multimedia
 dvd field:      dvd:///dev/dvd

This last from the useful-looking blog:

  [http://boff.wordpress.com/](http://boff.wordpress.com/)

---

### Post by TH3_D0ct0R on 2007-03-11
i had all of these same problems, and read all of this and, idk who but someone said to just download new player....so i proceeded in doing that and it work, i had the lidvdread and stuff installed and then i install Xine Movie player and it works like a charm. 
i also install okle and ogle and thodden dvd ripper, and kaffine, i choose Xine over all of these becuase it looks pretty much the same as power dvd (which is what i used earlier) 
but kaffine worked for me and i didnt try anything else out but that is the only solution i have come up with and it works prefectly, altought hey dont work in totem but thats alright

so i recomend downloading Xine movie player through your ubuntu Add/Remove... app


if it doesnt work or you dont understand just respond or pm me or sumthin

---

### Post by alorenzatti on 2007-04-05
Hi there

for:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found[/QUOTE]


I had the same error but the problem was that it's a wrong path

The correct one is:

sudo /usr/share/doc/libdvdread3/install-css.sh


Hope it can help u

cheers
Andres

---

### Post by adastra23 on 2007-04-05
I too am having trouble with Totem or mplayer playing dvd's. 
Tried all the suggestions on this thread.
I installed easyubuntu and after cleaning up my sources.list, I was able to get that to install codecs, plugins, what have you.
VLC media player works.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

good enough for me. :KS

---

### Post by xrdguy on 2007-07-30
it worked for me.. thanks.. i m in region 1. canada for RPC

---

### Post by troykm on 2007-08-19
Hi all,

I am new to this forum and Ubuntu.

After weeks of trying i figured out how to get Dvds to play, and i have put an easy step by step guide on my blog  [www.linuxitis.blogspot.com](www.linuxitis.blogspot.com)

this guide is for people who, like me, are not tech heads who need simple instructions. (not that im simple or anything :lolflag:)

I think this is the easiest way to do it and i hope this helps others

ps: love all the support sites for Ubuntu, i hope my small contribution adds to this vast support network.

cheers

Troy

---

### Post by linuxisgod on 2007-09-15
i Just Wanna Thank All of yall For Posting up links and helping people 


thanks alot keep up the feeds

---

### Post by bayosidikiba on 2008-01-28
I will need go to Application->AddRemove and search for VCL and select it, then apply for the installation.
after installtion, you will find the shrtcut in Application->Sound & Video->

---

