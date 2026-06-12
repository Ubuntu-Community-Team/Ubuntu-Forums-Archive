---
title: "HTML editor, IM and media player"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Mr_JMM on 2007-10-02
Hi,

Please do say or move this if this is in the wrong forum....

Part of my decision on what distro I use will be based on what I use my laptop for.

I'm a self-employed website designer / developer and have three requir..., er four requirements of an OS:
- A good HTML editor (I'm a self-employed website designer/developer). I design/develop in code so I don't need anything as fancy as Dreamweaver but coloured script would be nice.
- A graphics application. This is probably the most demanding software I need. I use Fireworks and use most of it's capabilities!
- I do a lot of instant messaging currently with WLM (Windows Live Messenger). I need an IM that will allow me to chat to people that still use Windows based IM's.
- I listen to a lot of music and as much as I love my SE Walkman phones, a good Media player would be good (basically, needs to be able to rip and support mp3 with a good library system).

My question is then, will I find the above with Ubuntu? Would I be better off trying to run them as Windows *spit*spit etc.* applications in something like Wine?

Many thanks as always,

James

PS. In around-about way the above is tied a bit with the choice of Ubuntu variants(K/X/Ubuntu) and I make this comment:
*Reading about k/x/ubuntu I gather I'm best just to try them but Ubuntu has a great community and seems to me (from a complete newbies POV) to be the most supported and it should run ok on my poor old 1.1GHz 256MB laptop (although Xubuntu may be faster, I'll compare them).*
...but please feel free whether to include this last part in your answer or not.

---

### Post by mridkash on 2007-10-03
**HTML:** BlueFIsh Editor
**CSS:** Cssed
**Graphics:** GIMP (for 2d), Blender (for 3d)
**IM:** Gaim (able to add MSN) already shipped with ubuntu Live CD
**Media Player:** Rythmbox (iTunes like) , Amarock (very Advanced with lots of features).

Your Laptop fulfills minimum requirements for Ubuntu.

---

### Post by Mr_JMM on 2007-10-03
Many thanks, cheers.

Will try and have a look at those later today (need to sleep sometime!).

Is there a HTML/CSS/PHP all in one program?

---

### Post by rsambuca on 2007-10-03
> **Mr_JMM said:**
> 
PS. In around-about way the above is tied a bit with the choice of Ubuntu variants(K/X/Ubuntu) and I make this comment:
*Reading about k/x/ubuntu I gather I'm best just to try them but Ubuntu has a great community and seems to me (from a complete newbies POV) to be the most supported and it should run ok on my poor old 1.1GHz 256MB laptop (although Xubuntu may be faster, I'll compare them).*
...but please feel free whether to include this last part in your answer or not.

One of the biggest things to consider when using an 'older' (no offense!) machine like this is to try and not use programs that use different libraries, especially KDE and Gnome ones at the same time.  If you do, both sets of libraries will need to be loaded, and with 256 MB RAM, you will need to use your swap which will really s l o w down your performance.

I like the previous poster's suggestions, but I would probably skip amarok (as good as it is) and stick with Rhythmbox if you use Ubuntu.

---

### Post by mridkash on 2007-10-03
BlueFish is all (HTML, PHP, CSS, C etc) in one.

Also Ubuntu's no frills default editor (Gedit) is good with syntax highlighting of many different languages.

---

### Post by Incense on 2007-10-03
First I would invest in some more RAM. 

HTML + CSS + PHP= Quanta
Graphics = Krita
IM = GAIM
Music = XMMS (Amarok if you get more ram)

I would not want to use Krita or Gimp though with only 256 unless you run Xubuntu. Then it may be ok. Just my .02

Cheers!

---

### Post by rsambuca on 2007-10-03
> **Incense said:**
> First I would invest in some more RAM. 

HTML + CSS + PHP= Quanta
Graphics = Krita
IM = GAIM
Music = XMMS (Amarok if you get more ram)

I would not want to use Krita or Gimp though with only 256 unless you run Xubuntu. Then it may be ok. Just my .02

Cheers!

I wouldn't use Quanta or Krita on your rig as they will both pull in kdelibs.

---

### Post by Incense on 2007-10-03
> **rsambuca said:**
> I wouldn't use Quanta or Krita on your rig as they will both pull in kdelibs.

Good call. Didn't really consider that.Too bad really since they are amazing apps. Guess I would go for gedit for syntax then.

---

### Post by mcduck on 2007-10-03
Web pages: Gedit. Just enable couple of plugins to add the features you want. And install the gedit-plugins package to get more plugins..

Graphics: Gimp + Inkscape (and Imagemagick if you need to process large amount of images)

IM: Pidgin

Music: Rhythmbox, Exaile, Listen!.. Choose the one you like the best. If you don't mind using a separate program for ripping then Grip+MPD would be a great choice, and ncmpc or Sonata as client for MPD.

---

### Post by meborc on 2007-10-03
if you are going to multitask (and you probably are) it is a good idea to look into cli (terminal) programs with no graphical interface... for example cmus as a mp3 player... why would you need a graphical interface for something you just listen at while doing other stuff :) and finch for IM...

just an alternatives to keep the ram usage low

---

### Post by Mr_JMM on 2007-10-03
Cheers for all the replies. Lots to look at then.

> One of the biggest things to consider when using an 'older' (no offense!) machine like this is to try and not use programs that use different libraries, especially KDE and Gnome ones at the same time.
Being new to all things Linux, how do I know what libraries a program will use?

> I wouldn't use Quanta or Krita on your rig as they will both pull in kdelibs. 
Sorry, what are "kdelibs"?

> First I would invest in some more RAM.   
One of the reasons I'm looking into a Linux OS is so that I don't have to upgrade my Laptop. Also, this implies that these programs will be a bigger strain on my system than the programs I already have which again, would pretty much kill any chance of me converting to Linux in an instant.
At present I run Dreamweaver, Fireworks, Firefox, Thinderbird, Windows Live Messenger on the laptop all at the same time with no running problems what-so-ever!! Please tell me you're suggestion is based on a wildly exaggerated concern.

---

### Post by rsambuca on 2007-10-03
> **Mr_JMM said:**
> Being new to all things Linux, how do I know what libraries a program will use?Ubuntu uses a package manager called 'apt' which handles everything for you.  There is a graphical interface to apt called the "Synaptic Package Manager".  If you want to install Thunderbird, for example, you would just open Synaptic, select Thunderbird for installation, and click "Apply".  Then Thunderbird, plus all of the packages it requires as dependencies are also installed if required.  If you want, you can view the dependencies and libraries for any program prior to installation.  There is a "Properties" tab that you can press to see what dependencies and/or libraries it will use.
> Sorry, what are "kdelibs"?Those are the libraries that the KDE (QT) desktop uses.  Gnome uses a different set of libraries (GTK).  Most people nowadays use a mixture of KDE apps and Gnome apps, as they work fine in both Desktop environments.  In your case, however, you may run into slowdowns if you run mixed libraries due to low RAM.

> One of the reasons I'm looking into a Linux OS is so that I don't have to upgrade my Laptop. Also, this implies that these programs will be a bigger strain on my system than the programs I already have which again, would pretty much kill any chance of me converting to Linux in an instant.
At present I run Dreamweaver, Fireworks, Firefox, Thinderbird, Windows Live Messenger on the laptop all at the same time with no running problems what-so-ever!! Please tell me you're suggestion is based on a wildly exaggerated concern.Linux will run fine on older hardware, in fact much better in general than Windows.  Ubuntu is not the lightest of distros though  so you should be aware that your machine is on the low-end for minimum specs for Ubuntu.  As for your program needs, Firefox and Thunderbird have native linux versions, so they will be exactly the same.  There are many html editors like bluefish, and for messenging, you can use the default gaim.  My recommendation is that you stick to the default programs as much as possible so that you are sure that you are not mixing your libraries too much.

---

### Post by Incense on 2007-10-03
I don't know why this escaped me, but I am typing this on a machine running Kubuntu 6.06, with a P4 and 256mb of ram. Quanta, Krita, and Amarok all run just fine on this machine. They are native apps for this DE which I'm sure helps, but I just thought I'd throw that in. 

As a side note, I couldn't get the 7.04 live cd to run on this machine. It was just unusable in both Gnome and KDE. I don't know if maybe 6.06 has less overhead, or really what the deal is. Just something I noticed though.

---

### Post by Mr_JMM on 2007-10-03
rsambuca : Thanks. I think I understand.

To all: Many thanks for your help. I will be asking a lot of questions but I wanted to say that you have all made me feel very good about the whole linux experience, especially Ubuntu. I admit I'm also playing around with Zenwalk but Ubuntu will always be on my main drive!!

Thanks again and I look forward to exploring more of Ubuntu.

Will try out the programs recommended as soon as and will let you know how I get on (that'll be niiiiiiiiice.....)

---

