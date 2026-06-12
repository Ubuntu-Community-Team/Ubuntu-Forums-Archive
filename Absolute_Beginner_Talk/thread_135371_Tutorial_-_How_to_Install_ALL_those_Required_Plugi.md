---
title: "Tutorial - How to Install ALL those Required Plugins in Mozilla Firefox (Web Browser)"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-23
Hello all!

I have more "Tutorial" contribution from me:


**_Tutorial - How to Install ALL those Required Plugins in Mozilla Firefox (Web Browser)_:**


_For Ubuntu 5.10_:


_Prerequisites_:
You should know how to use & work with the "Synaptic Package Manager" program.
If you do NOT have good knowledge of the above mentioned program, please go inside the Ubuntu's "Customization Tips & Tricks" Page & look for the Tutorial I have created, named:

"Tutorial - How to get those valuable ".deb" Program Files & Back Them Up" (Article #: 134914)
OR click here: [http://ubuntuforums.org/showthread.php?t=134914](http://ubuntuforums.org/showthread.php?t=134914)


_Story_:
I once wanted to be able to view Apple's Quicktime Movie Clips (Streaming Video files), but NOT the kind that you download into your Ubuntu & you can view it later, whenever you want, but the kind of Streaming Video that you view it through (or within) the Mozilla Firefox's Internet Browser window.

So I went in the Forum & made a post on this.
I got many answers, but NO answer stated specifically what I really needed to install.

_Outcome_:
Eventually, if you go & install 10 or 12 programs in your Ubuntu, (some people suggested), at some point you are FOR SURE going to be able to view your  Apple's Quicktime Movie Clips...
... however, you will _also_ NOT realize which program made it work or if it were actually a combination of programs that made it work or something else... (maybe a "miracle"!) ...

In the end you will feel like the "guinny pig"(how do you spell that?), where you are going to try anything (anybody) suggests to you, to finally get your job done...  

But do you really want to install SO many programs, while you can get what you want by just installing ONLY 2 programs?

At the same time I ALSO wanted to speak about OTHER required Plug-ins people would need in their Mozilla Firefox Internet Browsers.


In this Tutorial, I will explain in FULL all the needed steps to Install the following Mozilla Firefox's Plug-ins:

1. MPlayer Plug-in - for Mozilla Firefox (Internet Browser) - _Package Name_: **mozilla-mplayer**

2. The "w32codecs" - _Package Name_: **w32codecs**

3. Sun's Java 2 Runtime Environment Plug-in – for Mozilla Firefox (Internet Browser) - _Package Name_: **j2re1.4-mozilla-plugin**

4. Macromedia's Flash Player – for Mozilla Firefox (Internet Browser) - _Package Name_: **flashplayer-mozilla**


_Note 1_:
As I mentioned before, you should know how to use & work with the "Synaptic Package Manager" program.
If NOT, go back up (in the beginning of this Tutorial) in the Prerequisites section, read the Prerequisites, and go search & READ through that Tutorial I made, cause you will need it.

Besides, I did NOT make it for me, but for YOU newcomers.

It may ALSO be required (I am NOT sure about this), in order to make all the above packages available in your "Synaptic Package Manager" program for Installation, that you MAY have to tamper your "sources.list" File, inside your Ubuntu's "/etc/apt/" Folder.

_In Brief, let me explain_:
If you launch "Synaptic Package Manager" program, you will notice on your "Status Bar", that the Packages available for installation from the Ubuntu Community are "4.092 packages listed – 1.033 installed" (if you have Ubuntu 5.10 installed).
 If you had tampered your "sources.list" File, you could get  on your "Status Bar", "17.824 packages listed – 1.033 installed", if not more...
That means that thousands of programs (authenticated or not) are available for you to install through the "Synaptic Package Manager" program.

	... isn't it nice to have lets say 5.000 programs (I am NOT including packages 
            designed ONLY to make other programs work properly) that are offered to 
            you for FREE (to download & install), in your Ubuntu Computer, while in 
            Windows, you are ONLY given 10 (or 20) programs overall & for the rest YOU 
            have to pay on an Per-Program basis...
	... aren't you getting ECSTATIC now about Ubuntu or what?

_Note 2_:
This Tutorial's main objective is NOT to teach you how to MAKE available to your "Synaptic Package Manager's" MORE program packages, but to teach you How to Install Mozilla Firefox's (Internet Browser) Plug-ins.
Look at a different Tutorial for this (I currently have NOT made one yet, but probably some other person has – take a look at the Ubuntu's "Customization Tips & Tricks" Page & hopefully you will find one).


**_Part 1 – Installing the MPlayer Plug-in - for Mozilla Firefox (Internet Browser)_:**

The first thing you will want to ask me, is:

Why do I want this Plugin?

Well, if your Ubuntu is NEWLY installed, it does NOT install (by default), this Plugin to be available to your Mozilla Firefox (Internet Browser).

So, launch a window of your Mozilla Firefox browser & go visit the following Internet page:

	[http://www.pixar.com/featurefilms/ts/theater/index.html](http://www.pixar.com/featurefilms/ts/theater/index.html)

	_Note_:
	The "Warner Brothers" film making company, also Requires (in some cases) 
        the MPlayer Plug-in to let you watch their upcoming Movies releases in 
        Streaming Video from inside your Mozilla Firefox (Internet Browser)...

So, you want to watch the trailer of that old but famous Pixar's "Toy Story"?

Why don't you click under the "Teaser Trailer", the "240x180" one, to watch the Streaming Video from within your Mozilla Firefox (Internet Browser)...

If you have a CLEAN Ubuntu install (meaning that you have just installed Ubuntu but NO other programs), you will probably get a window saying the following: "Totem could not play 'fd://0'" ("Totem" is Ubuntu's default pre-installed Movie Player). Close that window & press on the (Site's) green "Exit" button, to return to the previous Page, the one you first visited.

What happened to your Mozilla's Firefox window?

Did you get the result I got?

My Mozilla's Firefox (version 1.0.7) window unexpectedly closed...

I had to re-launch the Mozilla Firefox Browser window, type that Internet Address again, to go visit that page...

So, what is the problem?

Basically to see this Apple's Quicktime Movie Trailer, you NEED the MPlayer Plug-in - for  Mozilla Firefox (Internet Browser).

How can you get it to install?

Launch your "Synaptic Package Manager" program & perform a "Search" for the program "**mozilla-mplayer**".

Go on & install this program.

_Note_:
Again, I assume that YOU know how to work with the "Synaptic Package Manager" program.
If NOT, I suggested before, to go & read My other Tutorial –  Article #: 134914.
OR click here: [http://ubuntuforums.org/showthread.php?t=134914](http://ubuntuforums.org/showthread.php?t=134914)

Some people (people with better knowledge), will probably say:

	Why don't I use my other Method to install ".deb" Packages?
	... I will just use "Synaptic" to get the ".deb" Packages, &...
	... instead of installing them using "Synaptic", I will use the classic old  "dpkg -i 
            filename.deb" method.
	... and I will search for dependencies with the other classic "dpkg -I 
             filename.deb" method, &
	... after I find the order in which I will have to install dependency files, 
            everything will end up ... great...

And they will probably install their programs with NO problem...

However, if they EVER decide to "Uninstall" their programs:

If they are lucky, the program they installed, should have some "Uninstall" ReadMe file or an "Uninstall" button somewhere in the Program's Menu...

If NOT, then they would have to try-out (or experiment) their way to "Uninstall" that program.
... and of course, NO one can assure them that they "Uninstalled" the right way or that they have left some packages behind or that they have even deleted possibly wrong stuff (in the case of a Newbie...)

However, if they had used the "Synaptic Package Manager" program, from the START, they could have easily "Uninstalled" their program in a nice, clean & straightforward way.
The "Synaptic Package Manager" program, does NOT care if the program (you are installing) has an embedded "Uninstall" option.
"Synaptic" keeps track of every install step (the program you are installing makes), so when the time comes you want to "Uninstall", it knows exactly what it needs to get rid off.
But that does NOT mean that you SHOULD start installing a whole bunch of Programs, (without caring whether you really need them or not), & then rely totally in "Synaptic" to clean you up from ALL the "junk" (& trouble) you installed...
"Synaptic" is just a program & it is designed to work perfectly 99.99% of the times.
So, do NOT push it to its limits & get the 0.01% chance to "mess" your system... 
And try NOT to install junk!
Compared to the Windows world, you will eventually find that your Ubunty is much more STABLE, FAST & RELIABLE.
Your problems (crashes, etc.), are going to be VERY little, but it does NOT mean that they do not exist...
Every OS maker would hope to achieve this level, but STILL it is very hard to be achieved by anyone...


_Back to the Part 1_:
You have installed the program named "mozilla-mplayer".

Why don't you go back now & try to see that famous Pixar's "Toy Story" Movie Trailer (created in the Apple's Quicktime format)?

_Result_:
Assuming that you have a CLEAN Ubuntu install, you should NOW be able to view the Streaming Video from within your Mozilla Firefox (Internet Browser), but with NO sound.

So what do YOU do?

Well, you need to install those "w32codecs".


**_Part 2 - Installing the "w32codecs"_:**

_(Before you Install) Note_:
If you enter a Forum & post a "Please help me install the "w32codecs", you will get a reply:

	Please go read the "Wiki" page, on Restricted Formats:

	[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

_In a few words_:
I am NOT sure about Quicktime specifically, but I assume it's similar to MP3 as far as the legalities go. 
So (as I understand it), the deal with "mp3" is that it's patented technology & if you write any software that plays mp3s you have to (in the US at least) pay a small License fee to the patent holders for each copy of the software you distribute.
When you buy a copy of Windows, for example, the fee for using "mp3" & several other proprietary formats is included in the cost.
Since Ubuntu is distributed for Free, obviously they can NOT afford to pay for a license for each person that installs Ubuntu.
That's why a lot of multimedia does NOT work "out of the box" with Ubuntu. 

In some countries, the law does NOT require such a fee, so you should check the laws for your country and see.
Also, as I understand it, if you own a copy of Windows (that you are NOT using on a different computer), you are allowed to install the "win32codecs" & use them legally.

If any of the above is not accurate, I hope someone corrects me...

_Outcome_:
Is it legal in YOUR country, for you to play these formats?
ONLY if your country's laws allow you to do so, should you play media using the "w32codecs".

OR: 

If you own a copy of Windows (that you are NOT using on a different computer), you are allowed to install the "win32codecs" & use them legally.


So, If you are OK with the above, go on & install in your Ubuntu the "**w32codecs**".

  
_Note_:
Keep in mind that the "w32codecs" you are installing are NOT Authenticated.
That means, that the program has NOT passed through extensive testing, to get a CERTIFICATION that there are NO problems or Conflicts or "whatever else" (with other programs), when using it...
Install & use the "w32codecs" at your own Risk.

Of course, if CERTIFICATION could GUARANTEE that EVERYTHING would work 100% Fine & with NO problems, then ALL Microsoft's Made products (which I assume have ALL passed CERTIFICATION), would create NO trouble to the Microsoft family Software...
Unfortunately, experience proves the opposite...
... however CERTIFICATION makes us ALL feel a little better!


If you are NOT OK with the above 2 REQUIREMENTS to be able to install the "w32codecs", I do NOT have ANY alternative to suggest to you.
I am sure that there are Always alternative ways to make your "sound" work, but I do NOT know any... (sorry, I am still a Newbie like you...).
Hopefully an Ubuntu PRO could help you out on this or hopefully Add a Post on this Tutorial with suggestions or better Add a step-by-step guide to show other possible directions...


After you installed in your Ubuntu the "w32codecs", go & visit again that famous Pixar's "Toy Story" Movie Trailer (created in the Apple's Quicktime format).

ALL should be working fine & you SHOULD be able to view the Streaming Video from within your Mozilla Firefox (Internet Browser), ONLY this time WITH sound.


**_Part 3 - Installing Sun's Java 2 Runtime Environment Plug-in – for Mozilla Firefox (Internet Browser)_:**

You will probably want to ask again:

Why do I want this Plugin?

Well, if your Ubuntu is NEWLY installed, it does NOT install (by default), this Plugin to be available to your Mozilla Firefox (Internet Browser).

So, launch a window of your Mozilla Firefox browser & go visit the following Internet page:

	[http://www.intel.com/products/motherboard/d865perl/index.htm](http://www.intel.com/products/motherboard/d865perl/index.htm)

The above Internet link takes you to Intel's Internet Site, on a specific Motherboard Page.

Inside that page, you will probably, see that there is a picture that you can NOT view, because you are missing a Plug-in – the "Sun's Java 2 Runtime Environment" one.

... and you will find a "click here to install plugin" button – only to find that it can NOT install in this 
    way...

_BUT REMEMBER_:
If you install Software with a different method rather than use "Synaptic", there is no go-back (or "Uninstall") option. It's only one way – & no way back!
Better do it with "Synaptic"...

Launch your "Synaptic Package Manager" program & perform a "Search" for the program "**j2re1.4-mozilla-plugin**".

Go on & install this program.

_Note_:
Again, I assume that YOU know how to work with the "Synaptic Package Manager" program.
If NOT (I suggested also before to), go & read My other Tutorial –  Article #: 134914.
Do NOT make me repeat myself...

Then inside your Mozilla Firefox's (Internet Browser) Standard Toolbar, click on the button named "Reload current page" (the equivalent to Internet Explorer's "Refresh" button – currently NOT "__fresh" but rather "Stinky" & "Rust(y)").

With the Internet Page "Reloaded", now you should be able to VIEW that nice Picture created for "Sun's Java 2 Runtime Environment" Plug-in.


**_Part 4 - Installing Macromedia's Flash Player Plug-in – for Mozilla Firefox (Internet Browser)_:**

You will probably want to ask again:

More Plugins?	... Oh NO !!! ...

Well, if your Ubuntu is NEWLY installed, it does NOT install (by default), this Plugin to be available to your Mozilla Firefox (Internet Browser), either.

So, launch a window of your Mozilla Firefox's browser & go visit the following Internet page:

	[http://www.nokia.com/](http://www.nokia.com/)

Look around inside that Internet Site & you will find that a Plug-in is missing.

	_Note_:
	The "Warner Brothers" film making company, also Requires (in some cases) 
        the MPlayer Plug-in to let you watch their upcoming Movies releases in 
        Streaming Video from inside your Mozilla Firefox (Internet Browser)...
	Other Companies, include:
	1. Canon
	2. Dreamworks
	3. Paramount Pictures
	... etc. etc. ...

This time, if you click on the "click here to install plugin" – you will find that it CAN be installed in this way!

_BUT REMEMBER_:
As I said before, if you install Software with a different method rather than use "Synaptic", there is no go-back (or "Uninstall") option. It's only one way – & no way back!
Better do it with "Synaptic"...

Launch your "Synaptic Package Manager" program & perform a "Search" for the program "**flashplayer-mozilla**".

Go on & install this program.


_Conclusion_:
You managed to install the required Plugins to make Your Mozilla Firefox Internet Browser capable to show you pretty much (& hopefully) everything out there... in the Net...

Hopefully there is NO other Plug-in missing to install.

If there is, write to me about it.
We would ALL like to know...

Give us an example too, so that we can see ourselves!


Have Fun !!!


P.S.1> Sorry for my bad grammar syntax (& repetitions), but I have spent more than 
           4 hours (this time) to create this... 
           ... excluding the Formats to my Ubuntu Hard Drive to find which (minimum) 
               combination of programs (installed) makes my Mozilla Firefox work "top 
               notch" ...
           ... hope it is helpful to you too!

P.S.2> I would appreciate if somebody has something to Add that corrects me if I 
           have performed a mistake.

	PLEASE do it however inside the Ubuntu's "Customization Tips & Tricks" Page, 
        as I have also Posted inside there.

	Unfortunately when I post there, there is always a lot of DELAY in my post & I 
        am left wondering whether the Post went right through or got dumped in the 
        proccess...

	So I always try to post a Tutorial here too !!! (just to be on the safe side) 

	At the same time inside the Ubuntu's "Customization Tips & Tricks" Page, 
        PLEASE do NOT add comments like "thanks dude", or "that's how you do it" 
        because people that want to read a Tutorial, end up reading comments of NO 
        Learning value.

	Here though, write as many comments as you like !!!

	Thanks !!!

---

### Post by WelterPelter on 2006-02-23
Or you can just use Automatix and it's... automatic.

---

### Post by neoflight on 2006-02-23
Interesting....

How about automatix and media player connectivity extension for Firefox?

---

### Post by Mustard on 2006-02-23
To be honest, I think the tutorial needs to be neater with less commentary/narrative.  If I was going to try a tutorial I don't think I would be interested in reading a 'story'.  The important parts of the tutorial are not easy to find ie the actual packages you need to install.

To summarise, I would:

1.  Cut out the narrative from the tutorial.
2.  Put the packages to be installed and the commands to install them inside forum codes [noparse]```
..text in here..
```[/noparse]

For example...

```
sudo apt-get install flashplayer-mozilla
```

---

### Post by BluenoseJake on 2006-02-23
Just the thing I was looking for, thanks a lot!

---

### Post by dvarsam on 2006-02-23
Dear Mustard:

Response:
Yes, but the Ubuntu Gurus ALWAYS recommend to do the Installations with the "Synaptic Package Manager" & not by the "Terminal".

Besides, you will need to know the exact name of the program you want to install, so that you can type it inside the Terminal & THAT you can find ONLY inside Synaptic (like the one YOU mentioned - e.g. "flashplayer-mozilla")


Are you suggesting that Newbies go out:

1. & memorize all the programs names they should type in the Terminal Command? 
    (because, Synaptic is the right place to find that the "flashplayer-mozilla " is the 
     name to type in the Terminal).
or

2. Do you prefer, instead of looking the exact program names through Synaptic & 
    then typing them on the Terminal, NEWbies ASK (instead) ALWAYS in the Forums 
    what to Type in the Terminal?

    I believe that reading through a Tutorial instead of NOTHING (or asking) is much 
    better!

    And I would be very happy if people in the "Customization Tips & Tricks" section
    would start to write stuff abou the Newcomers & NOT the experts...

    I have created many Tutorials, and I am still a Newbie...

   However, I am learning it the hard way, with posting questions, & I want to make 
   it easier for the newbies...

P.S.> I would be equally happy, if you can go & make your own descriptive version 
         or reply in FULL with your own version.
         Feel free, to take my version & adjust it the way you feel like to make a 
         "superversion" or Bible for the Newbies.
         Sorry, but it is easy to judge but hard to make or create...

---

### Post by mwanafunzi on 2006-02-23
Unless I misuderstood the tutorial, I thought dpkg had an unistall as in
dpkg deinstall, or dpkg purge. I have not really used these functions as of yet (as I have not used much of the terminal)... I was just hoping to get some clarification on what was said in the tut.

thanks

---

### Post by PerfectSelf on 2006-02-23
dvarsam, I think you are missing part of the point that Mustard was trying to make.

He never said that you should stick to just using the command line and apt-get to download packages. However, it would probably be helpful for people to learn the Synaptec way as you described as well as the command to be used in a terminal. 

Besides, the example he used was more of a comment on the formatting of your post. I agree with Mustard in that your guide, while helpful, is difficult to read. The information that the user really wants to know is hidden under and between mounds of excessive storytelling and extra whitespace. There's nothing wrong *per se* with creating a narrative to describe your point, but it becomes a hinderance in a few places in your post. In other words, I can't just scan the page and find the information I'm looking for. I have to read past information that isn't useful to me to find what I'm really after. Yes, I've figured out how to work Synaptec after your first point, I don't need to be reminded for a third and fourth time that you assume that I do know.

My advice would be to clean up your post to increase readability. The ALL CAPS words need to be lowercase. Remove unneccesary punctuation. Under each section, make separate and easily distinguishable subsections for the narrative and the solution. Provide clickable links for your readers to the websites you mention.

---

### Post by annazack on 2006-06-20
Hi there,
I tried with the flashplayer-mozilla (didn't exist) but instead I installed the nonfree-plugin and I still can't get pages that require flashplayer to work, what do I do next?

//Anna

---

### Post by thomasmilo on 2006-06-20
I wanted to say thank you and that I for one found the tutorial really very clear and useful.

---

### Post by dvarsam on 2006-06-21
Dear "thomasmilo",

Thanks for your encouraging reply!

I am glad it helped you!

Have fun with your ubuntu!

P.S.1> This HowTo used to be _also_ in the "Customization Tips & Tricks" section on this Forum, until somebody decided to go ahead & remove it from there!

P.S.2> I used to have many Tutorials there...

P.S.3> "Thank God" they did not remove it from the Beginner's Forum too!:D

---

### Post by dvarsam on 2006-06-21
Dear "annazack",

Thanks for your Reply!

[QUOTE=annazack]Hi there,
I tried with the **flashplayer-mozilla** (didn't exist)...

Instead I installed the nonfree-plugin & I still can't get pages that require flashplayer to work...
What do I do next?[/QUOTE]

Well, this problem is due to your Repos added in your **/etc/apt/sources.list** file!

You need to activate some of your Repos, so that you can perform a "search" on your "Synaptic Package Manager" & then locate & install the package you are looking for...

Please perform the following:

1. Launch a Terminal window (from Menu, select "Applications\Accessories\Terminal")
2. Type "sudo -i" (to log-in as "root" user)
3. Type your "password" (the one you use when you startup your PC)
4. Type "nano /etc/apt/sources.list" (to edit your "/etc/apt/sources.list" file)
5. Check if your "sources.list" file contains the following:
> # For Ubuntu v6.06 - Dapper Drake:
# -------------------------------

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper universe


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


## This was added (as  asked)
## Multiverse

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse


## This is required if you would like to install a Webcam.
## The Repo below, helps you locate & install the required package 
## named "easycam2".

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

## Backports:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


If your "sources.list" file does NOT contain any of the following, just add it in!

_Note_: The above "sources.list" file _contents_ apply for the Ubuntu **v6.06** - Dapper Drake version (the latest current version!).
IF you are using Ubuntu v5.10, you _must_ use a different "sources.list" file!

6. Type "Ctrl+X" (to save changes to your "sources.list" file)
7. Type "Y" (to save modified buffer)
8. Type "Enter" or "Return" key (on your Keyboard)
9. Launch "Synaptic Package Manager" (from Menu, select "System/Administration\Synaptic Package Manager")
10. Click on the button named "Reload"
11. Perform a "Seach" for the package you could not find before!

You should now be able to find/locate the package named **flashplayer-mozilla** & go ahead and install it!

Thanks for your response!

P.S.> If you still have problems, feel free to come back here & post!

---

### Post by WADemosthenes on 2006-06-21
Amazing tutorial, instead of going to different places to get pieces of information, all the specifics (and useful tests) are here.  I just have one small problem.  In firefox when I go to [http://www.pixar.com/featurefilms/ts/theater/index.html](http://www.pixar.com/featurefilms/ts/theater/index.html) and to the trailer it claims that I do not have the plugin.

---

### Post by maspiotis on 2006-06-23
Thanks for the great information, I wonder if you could provide a similar tutorial for Dapper Drake.  

  I love that you have included step by step instructions, that even a novice can follow, however it would make everything clearer if the instructions, (actual steps that need to be taken) were in bold type, and the rest of the text in normal type.

Thanks,
Michael

---

### Post by annazack on 2006-07-11
Hi,
first of all when i type sudo -i i get root without the password but when I type sudo -s I need the password...

Anyway: it says breezy badger 5.10 and I thought I had Dappar Drake since I did the upgrade?

How do I change that and after that, do you mean that I should change in the file so that it looks as your example in detail?

Thanks in addvance!

//Anna

---

### Post by PingunZ on 2006-07-28
**First enable Multiverse / universe.**
	
	Open a terminal and do:
```
	sudo gedit /etc/apt/sources.list
```
	there remove the "#" before the links
	save and close
	then do :
```
	sudo apt-get update && sudo apt-get upgrade
```

**Now install the plugins**
```

	sudo apt-get install mozilla-mplayer w32codecs j2re1.4-mozilla-plugin flashplayer-mozilla
```

That should do it.
Just copy/paste this into your first post ...
 Oh btw :: Automatix and Easyubuntu take care of this too

---

### Post by DougTheTyro on 2006-07-30
:KS [FONT="Arial"]Thanks for the help.  I enjoyed your wordy explanations.  I don't need or want to learn the intricacies of the terminal commands.  I just want to be prepared so I can divorce myself from the MicroSoft tyranny when Vista gets rammed down our throats.[/FONT]

---

### Post by jonrkc on 2006-07-30
> **thomasmilo said:**
> I wanted to say thank you and that I for one found the tutorial really very clear and useful.I agree with Thomasmilo.  Actually, I find the "narrative" approach to be refreshingly human.  But then I'm not a guru.

The Real Player mystery remains to be solved...  It worked under Hoary; not, at least for me, under Dapper despite installing the helix stuff everywhere I could think of.  Ah, well.  :(

---

### Post by ElderLars on 2006-08-02
I was doing all things you said about installing with synaptic. Its now intsalled. The problem is that i think it is installed with the old firefox and not with the new(1.5). The firefox iam using is installed in ./opt/firefox 
Do you have any idea how to solve this?

---

### Post by stanz on 2006-08-06
> **ElderLars said:**
> I was doing all things you said about installing with synaptic. Its now intsalled. The problem is that i think it is installed with the old firefox and not with the new(1.5). The firefox iam using is installed in ./opt/firefox 
Do you have any idea how to solve this?
I've always copied whats in the installed '**plugins'** folder, to my '*/opt/firefox/plugins*' folder.
The Default install firefox is in: */usr/lib/firefox/plugins* [I'm pretty sure?]
Copy ALL to: */opt/firefox/plugins* [you may have an extra 'firefox/' to add?]
Then.. you need to 'link' them all to: */usr/lib/mozilla/plugins/ *[B]or,
[/B]to Your '*home/firefox*' folder. Sorry- It's been awhile since I fiddled with it.
But, you should find a 'linked' plugin, in your /opt & point everything else you add- same direction !?
I hoped this helped, instead of confusing the question!
=======
For me also, I could not get : flashplayer-mozilla or w32codecs,
sources list attached~

---

### Post by Nightmist on 2006-08-09
Where is the "w32codecs"? Can't find it. I am still having problems getting sound from the clip. Also, I am having problems streaming .wmv files. Can you please update this guide to work with the latest version of Ubuntu?

---

### Post by Jagot on 2006-08-09
> **Nightmist said:**
> Where is the "w32codecs"?

[https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

---

### Post by Nightmist on 2006-08-09
Thanks. I did the...

wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)
and...
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

but still no sound on the Toy Story clip :/

[edit: Oooooops! Never mind! Everything is working! Firefox was using the VLC plug-in instead of mplayer. So after removing the former, it's all good! Thanks for your help!]

---

### Post by stanz on 2006-08-12
[quote=Jagot][https://help.ubuntu.com/community/Re...74003fde7daed5]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5")[/quote]
This calls for First Posting Edit/Update... ;)

---

### Post by aswells on 2006-10-09
Great tutorial! Liked the explanations that went with each package instead of just seeing "copy and paste this code and it will work"

---

