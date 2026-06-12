---
title: "Benefits of Ubuntu"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jp316ad on 2007-08-09
[SIZE="2"][SIZE="3"]Hey guys, I love these forums! You can get so much information from people who have truly tried and worked with Ubuntu. I am having trouble with Windows Xp and think it was becuz of a virus and now I am seriously thinking of switching to Ubuntu. I just want to do some research before I do. Are any of the programs compatible to Microsoft programs; such as the Open.org program compatible with Microsoft Word. I send documents over the internet as part of my work and this is important to me. If I send them something, will they be able to open it? 

Lastly what other benefits can you tell me to make the decision to switch. Thanks for your help. [/SIZE][/SIZE]

---

### Post by splintercellguy on 2007-08-09
Texas, eh? Not too far from you then :). Keep in mind that Ubuntu is NOT Windows, the point being that there's gonna be a bit of a paradigm transition. As for benefits, Linux is open and free, plenty of great apps, and OpenOffice.org can generate compatible documents. Try the LiveCD before you install.

---

### Post by jkblacker on 2007-08-09
Yup OpenOffice can save in .doc or .rtf format, both of which are compatible with MS Word, although sometimes some formatting can be lost when opening them. You could also persuade work to use Open Office on Windows, since there is a Windows version. It also has a built-in print to pdf function which you might find useful.

Other benefits: it just works. It doesn't have the problems Windows has (it has a few problems of its own sometimes, but if you're planning on just using it and not playing around with fiddly .conf files you'll be fine).

---

### Post by jp316ad on 2007-08-09
Well, honestly I'm getting sick of the problems I've had with Windows and I don't like Mac very much but a friend of mine got a laptop with Ubuntu installed in it; so that peaked my curiousity.

---

### Post by Jimmyfj on 2007-08-09
Benefits? They are, I believe countless. In terms of stability XP, and Vista has much to wish for, not to mention the degree of security build in at kernel level. Try out the Live Cd, its well worth working with, then decide if you want to install Ubuntu.

---

### Post by thefoolisme on 2007-08-09
Here's a brief list of similar/alternatives to Windows programs.  The list is by no means complete, but it's a good place to start.  

[http://www.linuxalt.com/](http://www.linuxalt.com/)

And as mentioned before, Open Office docs can be saved in Microsoft format, but there might be a slight format shift.  It appears that most versions of MS Office can be made to run with Wine ([http://appdb.winehq.org/appbrowse.php?catId=0](http://appdb.winehq.org/appbrowse.php?catId=0)), but I would definitely try OO first.  I would also make sure you get the compatible fonts installed in OO for MS.  That would definitely help with the formatting shift issues.  I don't remember the link, but if you do a search in the forum, you would find out how to do that.

---

### Post by splintercellguy on 2007-08-09
sudo apt-get install msttcorefonts I think.

---

### Post by Inxsible on 2007-08-09
> **jp316ad said:**
> [SIZE=2][SIZE=3] such as the Open.org program compatible with Microsoft Word. I send documents over the internet as part of my work and this is important to me. If I send them something, will they be able to open it? 

Lastly what other benefits can you tell me to make the decision to switch. Thanks for your help. [/SIZE][/SIZE]
Open Office has the option of saving files in multiple formats including the open source standard and microsoft .doc for word or .xls for excel files. If you use the microsoft extensions, then people using MS Office should be able to open/edit those files.

other benefits : Free Software for almost anything you want to do, provided you are willing to put in an effort to learn and install stuff :)

---

### Post by jp316ad on 2007-08-09
I tried out the Live Cd but the resolution on it was 800 x 600. Is this normal or can i change it to try it out better? If I can change it, how do I do that?

---

### Post by vexorian on 2007-08-09
Remember that ODF is an ISO standard and that there is a plugin for MSOffice available to be able to read it. So in short, you got all the right to use it and people got the obligation to have the plugin, it is not the opposite, MSoffice formats  are NOT standard.
> I tried out the Live Cd but the resolution on it was 800 x 600. Is this normal or can i change it to try it out better? If I can change it, how do I do that?Your graphics card will need you to install specific drivers.

---

### Post by splintercellguy on 2007-08-09
Yes. sudo dpkg-reconfigure xserver-xorg in Terminal. Follow the steps. Then press Ctrl-Alt-Backspace. This will be effective for the LiveCD session so you will have to do that again on the actual install. The reason we have to do this is that XFree86 does not have all that great detection of monitor v/hsyncs, and is a one-time step unless you change your display configuration.

---

### Post by Inxsible on 2007-08-09
> **vexorian said:**
> Remember that ODF is an ISO standard and that there is a plugin for MSOffice available to be able to read it. So in short, you got all the right to use it and people got the obligation to have the plugin, it is not the opposite, MSoffice formats  are NOT standard.
Your graphics card will need you to install specific drivers.

True, but how many MS Office users do you think even know about the ODF file format? Very few, IMHO.

But I wish everyone did, or rather MS Office changed its default to ODF (Yeah right !!)

---

### Post by cobrn1 on 2007-08-09
What are the specs of your pc please (so we know if you can run the liveCD, and what the graphics card is)?

---

### Post by jp316ad on 2007-08-09
I have a Dell Dimension C521. I'm at work right now so i'm not sure what the graphics card is: I know its something with NVIDIA (think its GeForce 6150, have to check to make sure, though).

---

### Post by splintercellguy on 2007-08-09
When you run the command I suggested, be sure to select whatever modes you want to be able to select, and make sure to allow the utility to detect the h/vsync settings.

---

### Post by hyper_ch on 2007-08-09
well, to find out what graphic card you got, open a terminal and run this command:

```

lspci

```

Somewhere among the lines it wil say what it is ;)

And why do you send .doc files? Why not PDFs? OOo has directly a PDF maker integrated ;)

A third alternativ would be to store the docs on [http://docs.google.com](http://docs.google.com) --> they can read ODF just fine :)

---

### Post by jp316ad on 2007-08-09
> **splintercellguy said:**
> Yes. sudo dpkg-reconfigure xserver-xorg in Terminal. Follow the steps. Then press Ctrl-Alt-Backspace. This will be effective for the LiveCD session so you will have to do that again on the actual install. The reason we have to do this is that XFree86 does not have all that great detection of monitor v/hsyncs, and is a one-time step unless you change your display configuration.


OK you lost me. In order to try out the Live CD - I have to reboot and press F12 to get to the boot screen from there the screen displays from where to which I select online cd rom *** (can't remember what else). After that I select start Ubuntu to which it boots into Ubuntu but the resolution is way too big. . . . .Ok from here what do I do to change the resolution??:confused:

---

### Post by jp316ad on 2007-08-09
I send them in Word documents because we send them several times back and forth and edit the document until we get a final draft.

---

### Post by splintercellguy on 2007-08-09
Type the commands in a Terminal window. Alt-F2 then xterm.

---

### Post by splintercellguy on 2007-08-09
Oh wait, I thought you said you could only select 800x600. If that's not the case, then just select a different resolution in System -> Preferences -> Screen Res.

---

### Post by deadgobby on 2007-08-09
OK if the CD runs live and you get video, sound, internet basics it will run fine with your system. If you do not get one of the following. You'll need to do some mojo to able to get Ubie to install. Your system is built around 2004 and most of hard ware detection should be OK. Unless your main internet connection is with a wifi card. As I stated run the CD and check out the major three. Video, Sound, and Internet. 
 To let you know up front and depending on where you live on this planet. All those fine CODECS such as WAV, MP3, DVD, and son on. Do not on will not work off the bat. You'll need to install all the goodies by your self. All the fun codecs cost money because they are Proprietary software
[http://en.wikipedia.org/wiki/Proprietary_software](http://en.wikipedia.org/wiki/Proprietary_software)
 and not open source. Thus if Ubie installed them on their O/S, Ubie would not be free and bla bla bla. Thus the it must be done by your own hands to install them. Its is "roll the eyes" illegal for you to do it. So personal use. Don't sweat it! When you sell systems with the CODECS installed. You where warned. 
 To install the restricted CODECS or known as formats. There is Automatix, Easy Ubuntu, and 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats). Automatix and Easy Ubuntu is 3rd party software and some people systems have broken after installing them. So you must every word for word on correctly doing so. 
 The main second problem is installing software. In the windows world you are looking for a exe file.  Well it is not the same in the Linux world and installing them can be easy....Some times.
You have the main four ways to install programs. 
1. Tarball AKA build from source 
[http://en.wikipedia.org/wiki/Tar.gz](http://en.wikipedia.org/wiki/Tar.gz)
2. RPM 
[http://en.wikipedia.org/wiki/RPM_Package_Manager](http://en.wikipedia.org/wiki/RPM_Package_Manager)
3. Deb 
[http://en.wikipedia.org/wiki/Deb_(file_format](http://en.wikipedia.org/wiki/Deb_(file_format))
4. Synaptic Package Manager
[http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
  Ubie is based off of Debian linux kernel and you'll find all sorts of programs to install that way. Synaptic is a easy and visual way to install programs and the very heart and soul the ease on working with Ubie. To get the cool programs you'll hear about adding "Extra Repositories" .
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
 Before installing software from the web like TAR or RPM is to look in Synaptic first. You'll see a big difference on the Synaptic program files after you enable extra repositories. 
I hope you I did not loose you here. 
See these links to install programs
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
 You'll all would see there is different desk top environments. Like Gnome, KDE, and XCFE or known as xwindows. Most people who are converting from XP like KDE, It has the same look and feel, but behaves totally different. You can try all three if you like by looking at this link 
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
 Then you can decide on what desk top environment you like as a desk top at the splash screen. Oh wow! I bet the doors of freedom are opening up there. Please do not ask what is best desktop environment. That is up to you. That is like you asking me what chicken taste like. It is up to you what you like. 
 The other most FAQ is virus, worms, and your systems being a zombie. 
To mess up a Linux box, you need to work at it; to mess up your Windows box, you just need to work on it.
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
 [http://librenix.com/?inode=21](http://librenix.com/?inode=21)

  OK lets look at this way. A windows virus or worm attacks the whole windows kernel or operating system. It is a monkey working and having lots of fun at your expense. Linux is built on lots of platforms.  You have the kernel as base, then the desktop, and so many doors and programs. Like when Neo of the Matrix walks into a hall way of many and many green doors. It gets lost and does not do any thing. Same with a Linux. Right now a Linux virus cannot attack the whole kernel. It only can effect a door. The five years of using Linux. I have yet to see one.
 
We are here to help you out and I thought do that for you
Gobby

---

### Post by jp316ad on 2007-08-09
LOL! You lost me about half way through but I'll reread it until I can understand this. I am kinda obsessive about this sort of thing and now that I know that there is a whole "new world" outside of Windows I kinda want to swallow it whole, if you get what I mean.

---

### Post by splintercellguy on 2007-08-09
Automatix is retarded, what are the repos for? :P I prefer VLC to skip the codec crap.

---

### Post by armandh on 2007-08-09
live will load it as default if it cannot establish better will work
I once used command line to add resolutions
sudo dpkg-reconfigure -phigh xserver-xorg 
it asks for video chip set then desired resolution

---

