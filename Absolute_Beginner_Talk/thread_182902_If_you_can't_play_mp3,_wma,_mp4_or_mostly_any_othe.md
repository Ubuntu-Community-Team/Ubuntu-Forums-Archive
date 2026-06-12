---
title: "If you can't play mp3, wma, mp4 or mostly any other codec read this!"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-05-27
Hi!

[COLOR="Red"]This post is hectically out of date! there is a more effective post here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624). If you still need help though read on! :)[/COLOR]

[COLOR="Blue"]
Seeing as this is not stickied anymore can people [COLOR="red"]please email me when you need help [/COLOR]on this post because I don't check it everyday! Send me a PM by Clicking on the big Orange RudolfMDLT selecting - send this user a personal message.[/COLOR]

I read about 3-5 posts a week on people new to Ubuntu not being able to play there media files. This post is intended to help people new to Ubuntu get their media playing.

The reason you cannot play your files is that they don't come shipped with Ubuntu, the reason being:

> Patent and licensing restrictions on media formats can complicate a free operating system's ability to distribute software that will support those formats. - Quoted from the Ubuntu WIKI

Giving the wiki a read is always a good idea!:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Please add the restricted, multiverse and universe repositories to your sources list before you continue. 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you're new to Ubuntu, and you wish for a quick fix, this application is a solution to most of your media troubles! You would really do yourself some good by using Easy Ubuntu:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Another life saver is Automatix.

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

Most users would want to install Automatix using option 2.2 

Both of the above install all of the codecs you need Plus the Firefox PlugIns for streaming media and the players needed for playing them and a whole lot of other things! 

Just one thing, if there is an option for installing new graphics drivers, like the saying goes, if it's not broken don't fix it! If you display works, UNTICK this option. Later when you are more comfortable with Ubuntu and the command line, then go messing around!

If you are new to the Linux world I suggest you do type out these commands or atleast copy and paste them. It will help you become comfortable with a text interface. On the forum it is much easier to say, "Copy and paste this..." than it is to explain to some one to open a cetain prorgam and explain 5 levels of diffrent GUI's. This is a benifit I believe Linux has over windows, you get tought to use a very effective tool like the terminal.

If you want to go it with the terminal:

Install the Xine streamer for gnome:
> sudo apt-get install gxine

Install all the Windows codecs that you're use to:
> sudo apt-get install w32codecs

Then a good media player, Amarok:
> sudo apt-get install amarok


For WMV files get Mplayer and all the Mplayer addons for Firefox!
> sudo apt-get install mplayer
sudo apt-get install mplayer-skins
sudo apt-get install mozilla-mplayer

I have found that some players cannot play the new WMV9 codec. Please install VLC to fix this problem!

> sudo apt-get install vlc

Although I prefer kaffeine for playing DVD's:
> 
sudo apt-get install kaffeine

If you have an IPod, you might need:
> sudo apt-get install ipodslave

Inorder to play DVD's:
> sudo apt-get install libdvdcss2

If you have troubles with some mp4 files:
> sudo apt-get install libmp4v2-0

For flash
> sudo apt-get install flashplugin-nonfree


Hope this helps!

Cheers,

Rudolf


EDIT: This thread has a grown a bit and I'll paste interesting stuff like new apps here that other users have found useful, in this post from now on.

Inetersting Stuff:

By Tobster,
> To get all your DVD's working also download Xine Movie Player from Synpatic Package Manager Xine as extra codec and quick time.

To be really cool you can watch ABC News on Ubuntu by downloading Democracy Internet TV player Automatix then download the ABC feed. 

By Artificial Intelligence

> Xpod you should know that nothing beat the VLC player, so it's quiet easy to choose 

By Peter41az

> automatix is great, automatix2 even better everything just works, like arnieboy touts!

Bleeder is awesome, if you have the video card to support it. 3d desktop even!

By Takmadeus

> Well.... here's the deal.... I had to reinstall ubuntu and then I looked for the add/remove software in the gnome menu.... just installed the codec pack featured in the multimedia section and then everything was good to go.... videos of every kind play like a charm now ;)



By Diggs
> 
I think that you guys need to take a step back and say
"why in the hell is it so freaking hard to play a ******* MP3 file in my poo brown operating system?"

and go from there
__________________

---

### Post by aresgoddess on 2006-09-09
what if stuff still won't play right? Like .ogm, .mkv, or .mp4 files? I have all the packages needed to play them (i think), and I still can't access the subtitles on the mkv files, the subtitles and alternate language audio on the ogm files, or play mp4 files at all.

This is what I have installed: w32codecs and libmp4v2-0. Might have some other packages installed, but right now, I have no idea.

Any advice?

---

### Post by RudolfMDLT on 2006-10-15
Sorry aresgoddess, I don't check back on old post's often. Please send me and email on the forum if you still require help! Thanks!

---

### Post by rlozano on 2006-10-15
nice post and very helpful for noobs Rudolf..

tnx.... :-D

---

### Post by RudolfMDLT on 2006-10-15
Everybody was a noob once! I just no the feeling so I try to explain EVERYTHING!  :)

Enjoy!

---

### Post by diepruis on 2006-10-15
Can someone sticky this?

---

### Post by RudolfMDLT on 2006-10-15
I would if someone told me how or whom to contact?

---

### Post by NeoLithium on 2006-10-15
Another easy way with an outstanding program, is to install automatix; which works very well, quickly, to get those codecs installed and setup for you.  I've used it on all of my Ubuntu installs, you can find the information on how to install it [here on their website.]("http://www.getautomatix.com")

There's good in-depth instructions regarding it; any many of the people on the board seem to enjoy it as much as I do.

---

### Post by diepruis on 2006-10-15
> **RudolfMDLT said:**
> I would if someone told me how or whom to contact?

I wouldn't know. I was hoping a moderator would see the request. If you are serious about asking someone, PM a forum mod.

---

### Post by Evergrey on 2006-10-15
I get following error after running EasyUbuntu.
After I run it all files should be downloaded right?

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


However I don't think that it has to do anything with my internet connection cause I succesfully downloaded amok player through Applications -> Add/Remove...
I'm not sure what is wrong :(

---

### Post by RudolfMDLT on 2006-10-15
When downloading packadges you sometimes need a form of verification. GPG is like a windows certificate. It's an electronic verification system. It has nothing to do with your internet connection.

What where you trying to download and after the download does it work, doesn't it work, did something disappear ect. A little more detail would help me help you. 

Thanks!

---

### Post by Perfect Storm on 2006-10-15
> **Evergrey said:**
> I get following error after running EasyUbuntu.
After I run it all files should be downloaded right?

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


However I don't think that it has to do anything with my internet connection cause I succesfully downloaded amok player through Applications -> Add/Remove...
I'm not sure what is wrong :(


More info: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by RudolfMDLT on 2006-10-15
wget [http://easyubuntu.cafuego.net/969F3F57.gpg](http://easyubuntu.cafuego.net/969F3F57.gpg) -O - | sudo apt-key add -

Open the terminal and enter the above command. See if this helps.

---

### Post by xpod on 2006-10-15
> Another easy way with an outstanding program, is to install automatix; which works very well, quickly, to get those codecs installed and setup for you. I've used it on all of my Ubuntu installs, you can find the information on how to install it here on their website.


Well it`s been 3 months for me and about 6 0r 7 installs on 2 different pc`s and Automatix is still the very first thing i install each time....A2 now

I do know how to install the other ways..(sometimes)but why go through all the hassle when 7 or 8 commands gives you access to all you could ever need in the way of multimedia...

The only trouble NOW is deciding which players to use cause i got a whole heap o them:mrgreen:

---

### Post by Perfect Storm on 2006-10-15
Xpod you should know that nothing beat the VLC player, so it's quiet easy to choose 8)

---

### Post by RudolfMDLT on 2006-10-15
I'll add the link to Automatix to the first post now, Thanks. I actually don't want to add Automatix or Easy Ubuntu because new users need to learn to get comfortable with the terminal soner or later....

---

### Post by Peter41az on 2006-10-15
i just got done installing automatix2, and automatix bleeder. automatix is great, automatix2 even better :) everything just works, like arnieboy touts!

Bleeder is awesome, if you have the video card to support it. 3d desktop even!

oh yes, the website addy: [http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Evergrey on 2006-10-15
> **RudolfMDLT said:**
> When downloading packadges you sometimes need a form of verification. GPG is like a windows certificate. It's an electronic verification system. It has nothing to do with your internet connection.

What where you trying to download and after the download does it work, doesn't it work, did something disappear ect. A little more detail would help me help you. 

Thanks!

I must say that I'm noob to linux, I finished my dual boot yesterday... and I have many problems right now, but I will stick to mp3 for now :)
Ok, first I followed link to easyubuntu download page.
Downloaded easyubuntu.deb (100.4 KB (102804 bytes))
I run that file then install it.
Next from Applications -> System Tools -> EasyUbuntu I tried to install flash, audio/video formats (restricted formats) and so on.
First I got error as described in previous post, later I installed "libdvdcss" from multimedia tab.. and that one is greyed out. (already installed) however I cannot install flash for example.. or support for mp3 I always get the same message.
I must say that I'm doing my best to learn basics, but its pretty hard to understand all those terminal commands, so that probably wont help me much.
All I know is how to open it and some basic commands like cd, ls, startx and so on.

---

### Post by RudolfMDLT on 2006-10-15
I'm intalling the latest version of EasyUbuntu to see if I can regenerate your errors. Linux distro's such as Ubuntu or Mepis use central servers to store all the programs that are avaliable on that specific release. Easy Ubuntu uses the UPF dervers and the UPF as far as I know may be down. If I can't regenerate your errors or fix the problem, tell me what you want to install and I will explain how to do it...

---

### Post by RudolfMDLT on 2006-10-15
Easy is giving me troubles to, I have most of the software installed already and I'm not going to download all of it again. Seeing all the praise on this post for Automatix I would suggest that everybody that has trouble with Easy Ubuntu download automatix and use it instead. Welcome to open source => freedom of choice.

---

### Post by Evergrey on 2006-10-15
> **RudolfMDLT said:**
> I'm intalling the latest version of EasyUbuntu to see if I can regenerate your errors. Linux distro's such as Ubuntu or Mepis use central servers to store all the programs that are avaliable on that specific release. Easy Ubuntu uses the UPF dervers and the UPF as far as I know may be down. If I can't regenerate your errors or fix the problem, tell me what you want to install and I will explain how to do it...

For start I just need mp3 support and flash for firefox (1.5.0.3.)
p.s. Is there newer version of firefox?

---

### Post by RudolfMDLT on 2006-10-15
"Install all the Windows codecs that you're use to:
sudo apt-get install w32codecs"

I'll find the flah one now.

---

### Post by Evergrey on 2006-10-15
> **RudolfMDLT said:**
> "Install all the Windows codecs that you're use to:
sudo apt-get install w32codecs"

I'll find the flah one now.

Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

nothing changed

---

### Post by RudolfMDLT on 2006-10-15
Then it is installed! :) Still can't play mp3's? do you get any errors? or does the player start playing but no sound comes out? Check that you get sound at startup, intro music and such. open up a movie or anything that makes noise. Check that your speakers are on? :) volume control in ubuntu turned up?

for flash:

sudo apt-get install flashplugin-nonfree

What does this mean:

sudo: Super User DO: it's a security thing
apt-get: the aplication
install: what must it do? install, uninstall, remove
flashplugin-nonfree: what exactly it must install.

---

### Post by RudolfMDLT on 2006-10-15
I need to get studying for an exam so if my replies are few and far in between please excuse me for that. Sorry, but i really need to study! ;)

I won't let you hang though!

---

### Post by Evergrey on 2006-10-15
> **RudolfMDLT said:**
> Then it is installed! :) Still can't play mp3's? do you get any errors? or does the player start playing but no sound comes out? Check that you get sound at startup, intro music and such. open up a movie or anything that makes noise. Check that your speakers are on? :) volume control in ubuntu turned up?

for flash:

sudo apt-get install flashplugin-nonfree

What does this mean:

sudo: Super User DO: it's a security thing
apt-get: the aplication
install: what must it do? install, uninstall, remove
flashplugin-nonfree: what exactly it must install.

For FLASH:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

SOUND:
Yes I have startup sound (sound and everything with it works just fine). If I double click mp3 file it starts Totem 1.4.1 and get this msg:
"You do not have a decoder installed to handle this file. You might need to install the necessary plugins."

If I open it with amaroK which I downloaded through Add/Remove then it displayes song title, bitrate and lenght.. but nothing happens, no errors no sound.. nothing at all :(

---

### Post by RudolfMDLT on 2006-10-15
You need to add the restricted repositories:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I'll get back yo you on the sound issue.

EDIT: Totem doesn't have a lot to configure does it...
Did you install Xine as your engine? if not install it, the instructions are up top. try playing it trough amarok and under settings => configure amarok move to the engine option and tell me what engine you are using. Set your output to alsa and your speaker arrangment to Steoro 2.0.

---

### Post by Evergrey on 2006-10-15
> **RudolfMDLT said:**
> You need to add the restricted repositories:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I'll get back yo you on the sound issue.

EDIT: Totem doesn't have a lot to configure does it...
Did you install Xine as your engine? if not install it, the instructions are up top. try playing it trough amarok and under settings => configure amarok move to the engine option and tell me what engine you are using. Set your output to alsa and your speaker arrangment to Steoro 2.0.

About restricted repositories:

I followed instructions but I still get errors:

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
](*,) ](*,) ](*,)

---

### Post by RudolfMDLT on 2006-10-15
[COLOR="Red"]{PLEASE NOTE: THIS LIST IS FOR DAPPER - EDGY USERS LOOK IN PAGE 6}[/COLOR]

This is very unorthadox(ignore the spelling :rolleyes:  ) but open your sources file with the sudo command. Save it as another file you can find later as a backup, afterwards, select everything and press delete, yes, do it. :) paste the following in to the sources list and save it.

> 

deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper main restricted
# # Major bug fix updates produced after the final release of the
# # distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# # Uncomment the following two lines to add software from the  universe 
# # repository.
# # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# # team, and may not be under a free licence. Please satisfy yourself as to
# # your rights to use the software. Also, please note that software in
# # universe WILL NOT receive any review or updates from the Ubuntu security
# # team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper universe
# # Uncomment the following two lines to add software from the  backports 
# # repository.
# # N.B. software from this repository may not have been tested as
# # extensively as that contained in the main release, although it includes
# # newer versions of some applications which may provide useful features.
# # Also, please note that software in backports WILL NOT receive any review
# # or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


you might need to append the automtix source after words but do that later, this is a clean Ubuntu source list. Give it a try.

---

### Post by Evergrey on 2006-10-15
> **RudolfMDLT said:**
> This is very unorthadox but open youre sources file with the sudo command. Save it as another file you can find later as a backup, Afterwards, elect everything and press delete, yes, do it. :) paste the following in to the sources list.



you might need to append the automtix source after words but do that later, this is a clean Ubuntu source list. Give it a try.

I will try this later.
Just some info to add...
I tried running easyubuntu again and download restricted audio formats... I got same error messege but download started anyway.
This is very strange. Why is this happening? Server busy or something else?
I can play mp3 files now. :-k

---

### Post by RudolfMDLT on 2006-10-15
Easy Ubuntu installs 100's of packdges each time. Either you made a typo when editing it, or the Linux Fairy screwd with your box(this is tech talk for I don't really know :mrgreen: ), or, the reason I think: Easy Ubuntu uses the United Peguin Front's servers for it's repositories. The UPF is has stopped it's service so that could be part of the problem. But hey, if you find you can't play something or you're looking for an application, open synapic, search for the program and download it. Easy Ubuntu makes life easy, but when it does break we have no way to know what really went wrong. I can speculate that EU downloaded the Win32Dodecs but not all of them or not all of Xine's dependicies and thus causing Win32Codecs to be displayed as installed but they still need Xine and ALL of Xine's componets to function. 

Anyway I'm glad that they are working.

Cheers,

Rudolf

---

### Post by gn2 on 2006-10-15
Just don't understand why all this stuff isn't included and has to be added later.

Other Distros seem to, so just exactly why can't Ubuntu?

More info please.

---

### Post by Perfect Storm on 2006-10-15
It's because Ubuntu is free (as in beer and in speech). Alot of thte codecs, special applications aren't free.
[http://www.ubuntu.com/ubuntu/philosophy](http://www.ubuntu.com/ubuntu/philosophy)

---

### Post by Evergrey on 2006-10-15
> **RudolfMDLT said:**
> Easy Ubuntu installs 100's of packdges each time. Either you made a typo when editing it, or the Linux Fairy screwd with your box(this is tech talk for I don't really know :mrgreen: ), or, the reason I think: Easy Ubuntu uses the United Peguin Front's servers for it's repositories. The UPF is has stopped it's service so that could be part of the problem. But hey, if you find you can't play something or you're looking for an application, open synapic, search for the program and download it. Easy Ubuntu makes life easy, but when it does break we have no way to know what really went wrong. I can speculate that EU downloaded the Win32Dodecs but not all of them or not all of Xine's dependicies and thus causing Win32Codecs to be displayed as installed but they still need Xine and ALL of Xine's componets to function. 

Anyway I'm glad that they are working.

Cheers,

Rudolf

Thanks for all advice mate.
However I'm still having issue with flash in firefox... I downloaded flash with easy ubuntu... and it's not working anyway. Do I need new version of firefox or something? (current is 1.5.0.3)
One more thing... after some time my internet connection stops working, then I have to restart to make it work again. It's pretty annoying... but I guess it doesn't belong in this thread anyway :-#

---

### Post by thelinux_guy on 2006-10-15
I think this might be easier,Go to the package manager (not the advanced one)
Click "unsupported applications" and then go to "sound & video" Now look for 'Gstreamer Extra Plugins" and "Gstreamer ffmpeg Video Plugins"I installed these last night and they work fine(I guess there supported?)After you install them,you should be able to play formats like mp3,ogg.wma,wma,ect

---

### Post by tc5440 on 2006-10-15
Which package manager do you mean?? I have Synaptic only and it does not have an option for "unsupported applications"??

---

### Post by jrz on 2006-10-15
I installed VLC player the other day and have tried several videos using various formats including a couple I have never heard of and had no problems and did not have to search out and install any codecs. Subtitles seem to be supported as well, so I have just associated all my video and audio files with VLC now. I just downloaded a video which noted that I would have to DL a codec to play it "Techsmith?" and it played as well without having to install any codec. I'm happy.

---

### Post by tc5440 on 2006-10-15
Thanks jrz, I have loaded vrc and it works great. How do I associate all of me audio & video with vrc?

---

### Post by Perfect Storm on 2006-10-15
Right click the desired file type you want VLC to play and click properties. Go to "Open with" tab. If VLC isn't list there, click the "add" button. Scroll down 'till you find VLC. and click ok. Now make sure that VLC is selected in the "Open With" window.

---

### Post by tc5440 on 2006-10-15
Thanks, that worked. Now for my next question.....

Any idea why the volume control in VRC and the main volume control run totally independently? The video is really quiet.

---

### Post by RudolfMDLT on 2006-10-15
Evergray, What website are you trying to use flash in? in firefox, click help and then about. The latest version is 1.5.0.7. If you have below this you can update here

[http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

Just reread, you are a bit out of date.

Though I doubt that FireFox is to blame.

Just post the website and we'll take it from there. If it's something personal you don't wan't the hole world to see email me by clicking on my avarter. (This does sound aquard but I've had this happen before...)

---

### Post by RudolfMDLT on 2006-10-15
In reply to what gn2 said - read the first post and then the wiki! ;)

---

### Post by Timmeh on 2006-10-15
Thanks for the solutions. :)

---

### Post by robinduncan on 2006-10-15
[QUOTE=RudolfMDLT;1057180]Hi!

I read about 3-5 posts a week on people new to Ubuntu not being able to play there media files. This post is intended to help people new to Ubuntu get their media playing.




Hi, I've been having similar problems to just about everyone on this thread. I've tried everything: 

easyubuntu [installed, but didn't work],

automatix [didn't install],

downloading individual applications through the terminal [fine, but flash not found],

downloading through through synaptic.

I've installed almost all the applications to do with multimedia that I can find, but I still cannot see multimedia flash stuff on youtube or googlevideo, or see all commercial DVDs (I have seen two, but they probably aren't very protected). 

I'm not sure if I have managed to enable the universe and multiverse repositories - when I look in software properties, they're both unchecked. When I try to add, there's always some error message or other, depending on whatever else i've been doing,such as: fiddling around in the sources;

- as suggested by rudolf [which produced a message about duplicate lines], 

- and as explained by the wiki

Can anyone see something obvious here that i'm doing wrong? very frustrating...
cheers,
robin

---

### Post by thelinux_guy on 2006-10-15
> **tc5440 said:**
> Which package manager do you mean?? I have Synaptic only and it does not have an option for "unsupported applications"??

The one where you go to the "applications" menu and then select "Add/Remove..." NOTE: Dont go System/Administration/synaptic package manager,Its not the right one

---

### Post by RudolfMDLT on 2006-10-15
Hi Robinduncan,

Okay, I take it you're new, this is how linux works:

There is a big pile of software on  a server some where, you have an app called synaptic on your machine and a config file called sources. This app uses the config file to find thses servers and then updates it's catalog of the software pile.

The error is in your Sources.list file. Obviously you have edited this thing because it no longer works! :) Thats okay. Here is a clean sources file to start off with:

> deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper main restricted
# # Major bug fix updates produced after the final release of the
# # distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# # Uncomment the following two lines to add software from the universe
# # repository.
# # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# # team, and may not be under a free licence. Please satisfy yourself as to
# # your rights to use the software. Also, please note that software in
# # universe WILL NOT receive any review or updates from the Ubuntu security
# # team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper universe
# # Uncomment the following two lines to add software from the backports
# # repository.
# # N.B. software from this repository may not have been tested as
# # extensively as that contained in the main release, although it includes
# # newer versions of some applications which may provide useful features.
# # Also, please note that software in backports WILL NOT receive any review
# # or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


open your sources.list

sudo gedit /etc/apt/sources.list

select all, delete and paste. I have added the line right at the bottom for Automatix. This will piont your computer to the Automatix repository.

Save the above file makeing double sure it looks like the one on the post.

then open ther terminal and copy and paste the following:

> wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
> gpg --import key.gpg.asc
> gpg --export --armor 521A9C7C | sudo apt-key add -

every single line must execute without error.
[COLOR="Red"]
You should then be able to find Automatix in synaptic, or if you wish:

> sudo apt-get update


> sudo apt-get install automatix2[/COLOR]

Try installing flash now. And afterwards, open up (EDIT:)) [COLOR="Red"]Automatix [/COLOR]and let it run.


This is the most help I can give now, I need to get to Varsity, I'll check back tonight.

Goodluck!,

Rudolf

---

### Post by Takmadeus on 2006-10-16
I have a question... don't really know if this is the right place (I am new to these forums)

I installes xine with all its dependencies, and win32codecs.... but whenever I try to play a video file it just says:

Codec de videoCodec de videoCodec de videoCodec de videoCodec de videoCodec de videoCodec de video: DivX 5 (DX50)

Continuar reproduciendo de todos modos?

translated into english it would be:

Video codecVideo codecVideo codecVideo codecVideo codecVideo codecVideo codec: DivX5 (DX50)

Continue playing anyway?

how can I solve this.... tried with totem (the normal totem, no totem-xine) and it just plays sound, no video at all....

please, help :) and thanks in advance :D

---

### Post by Perfect Storm on 2006-10-16
Try with mplayer and/or VLC

---

### Post by RudolfMDLT on 2006-10-16
Takmadeus, you might need to install the Xvid codecs, they are the opensource version of Divx. Just search for Xvid in Synaptic. Otherwise, mplayer is best for playing mostly anything.I've removed Totem from playing anything and I'm using Mplayer exclusivly because of all the wmv files I sometimes need to work with.

---

### Post by Takmadeus on 2006-10-16
> Takmadeus, you might need to install the Xvid codecs, they are the opensource version of Divx. Just search for Xvid in Synaptic. Otherwise, mplayer is best for playing mostly anything.I've removed Totem from playing anything and I'm using Mplayer exclusivly because of all the wmv files I sometimes need to work with.

> Try with mplayer and/or VLC

Thanks for the replies :)..... checking around it resulted that it could not find the divx decoding plugin... so I rechecked my repositories (I had to further edit sources.list) and when I reloaded the package list I was missing libxine-extracodecs (1.1.1+ubuntu1-2) and libxine1c2 (1.1.1+ubuntu1-2) I installed them and everything plays now.... yet xine seems to be a little jumpy and skipping frames.... is there any way to solve this?

---

### Post by janekw on 2006-10-16
See
[http://www.ubuntuforums.org/showthread.php?t=249305](http://www.ubuntuforums.org/showthread.php?t=249305)

---

### Post by robinduncan on 2006-10-16
> **RudolfMDLT said:**
> Hi Robinduncan,

Okay, I take it you're new, this is how linux works:

There is a big pile of software on  a server some where, you have an app called synaptic on your machine and a config file called sources. This app uses the config file to find thses servers and then updates it's catalog of the software pile.

The error is in your Sources.list file. Obviously you have edited this thing because it no longer works! :) Thats okay. Here is a clean sources file to start off with:



open your sources.list

sudo gedit /etc/apt/sources.list

select all, delete and paste. I have added the line right at the bottom for Automatix. This will piont your computer to the Automatix repository.

Save the above file makeing double sure it looks like the one on the post.

then open ther terminal and copy and paste the following:





every single line must execute without error.

Try installing flash now. And afterwards, open up compiz and let it run.


This is the most help I can give now, I need to get to Varsity, I'll check back tonight.

Goodluck!,

Rudolf


hi rudolf,
thanks for the advice. yes, I am new;)  I tried what you suggested, with little success:

1. after saving the new version of the sources file, should automatix not be installed, ie. show up in the applications menu under system tools?  It doesn't.

2. All the lines I was to feed into the terminal worked fine, but I didn't  manage to install flash: 

sudo apt-get install flashplugin-nonfree
E: Syntax error /etc/apt/apt.conf:4: Extra junk at end of file"

So, not much joy. btw, what is "compiz"?

cheers, 
robin

---

### Post by RudolfMDLT on 2006-10-16
Ah Robin, I'm sorry! In my haste I've left out the final set of instructions!

See the original post again and check the red corrections. 

Compiz is something you can play with later, for some reason I just wrote Compiz instead of Automatix. The instructions should have read that after the adding the security key's for the automatix repository you should be able to install it - either finding it in synaptic or from the terminal.

for furhter reading on compiz: [http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

I don't know whats up with your APT Config. I'll post mine and then compare it with yours. 

> Acquire::http::Proxy "false";

If yours looks just like mine except maybe for syntaxing(a missing comma or colon ect.) then just copy and paste mine over yours. If though, yours looks completely diffrent then post it and'll check it for errors. From the error I believe you're looking for something wrong either on line 4 or round and about line 1 coloumn 4 but it's just a guess.

Sorry for buggering you around with the Automatix instructions.

CHeers,

Rudolf

---

### Post by RudolfMDLT on 2006-10-16
> **Takmadeus said:**
> Thanks for the replies :) yet xine seems to be a little jumpy and skipping frames.... is there any way to solve this?

Hi!

Did you install the Xvid codecs? The movies that you are whatching, are they high quality DVD rips or are they crappy email quality? Sometimes, crappy encoding does screw around quality and accuracy of playback. What player did you use? or are all of them doing this?

---

### Post by Takmadeus on 2006-10-16
> Hi!

Did you install the Xvid codecs? The movies that you are whatching, are they high quality DVD rips or are they crappy email quality? Sometimes, crappy encoding does screw around quality and accuracy of playback. What player did you use? or are all of them doing this?

I used xine, and yes, I have all the xvid codecs.... they are videos with quite a lot of quality (HDTV rip) and in windblows they look just fine :(

---

### Post by RudolfMDLT on 2006-10-17
:-k 
:confused: 

In Mplayer, rightclick the play window and click preferences. Under

MISC: Enable cache
Video: check double buffering and Driect rendering.

What app in windows did you use to encode them? Honestly I have had some trouble playing some of my DVD rips, but nothing to do with skipping. My hunch still says encoder(Windows)-decoder(Linux) missmatch.

If you have the time, try recoding the video in Windows to just and older version of Divx using a 10% lower bit rate. I know this sound lke the a case of the tale wagging the dog but It's the only way i feel you can solve it! 

If you feel like it, start a new thread concerning this, the amount of people active in this thread seems to have dwindeled and my knowlodge about codecs seems to not be enough. Starting a new thread might get you some better answers! :) Sorry if it sounds like I'm ducking you but, rather that than the blind leading the blind. ;)

---

### Post by starfire1983 on 2006-10-17
Another, simpler way, to play some of the restricted formats is to install VLC Media Player. It plays just about anything you could want and you don't have to install anything codecs or otherwise. Don't get me wrong, the above suggestions are wonderful AND reccomended to do to make things even easier, VLC is really you're all-in-one player for anything, this includes .mkv, .ogm and other non-standard formats. This program is also available in Windows and Mac, if people are dual/tri-booting. [http://www.videolan.org]("http://www.videolan.org")

All it should require is (if not already installed):
sudo apt-get install vlc

---

### Post by adoy on 2006-10-17
Thank you for all the info guys. I'm glad I've found this forums. I'm still new here and need to explore the entire forums hehe.

---

### Post by Nactive on 2006-10-17
Hey,

I got this error when I try to install w32codec / mplayer:

thomas@thomas-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate


---------------

thomas@thomas-desktop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I already did "sudo apt-get update", but still have the same error ... :x

---

### Post by Perfect Storm on 2006-10-17
Make sure that your source.list is set up correctly.

---

### Post by RudolfMDLT on 2006-10-17
Nactive, type in the folowing commands to backup your sources list and then scroll through this thread and find the one that I posted here. Make sure that the universe and multiverse options are uncommented, ie, have no # before the URL. If you want you can just copy and paste mine and modify it as you need to further on down the road!

> sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
> sudo gedit /etc/apt/sources.list

---

### Post by robinduncan on 2006-10-17
> **RudolfMDLT said:**
> 

See the original post again and check the red corrections. 

 after the adding the security key's for the automatix repository you should be able to install it - either finding it in synaptic or from the terminal.


I don't know whats up with your APT Config. I'll post mine and then compare it with yours. 



If yours looks just like mine except maybe for syntaxing(a missing comma or colon ect.) then just copy and paste mine over yours. If though, yours looks completely diffrent then post it and'll check it for errors. From the error I believe you're looking for something wrong either on line 4 or round and about line 1 coloumn 4 but it's just a guess.

Sorry for buggering you around with the Automatix instructions.

CHeers,

Rudolf

Hi Rudolf,
thanks for your help again. I've tried what you suggested. Any attempt to download Automatix doesn't work: both the terminal commands produced this message again:
E: Syntax error /etc/apt/apt.conf:4: Extra junk at end of file

as did an attempt to open synaptic!

I tried "add/remove" in the applications menu, but that package manager wouldn't open either (not even a message to explain why)

I also tried the command:
[COLOR="Red"] 
Acquire::http::Proxy "false";[/COLOR]

but got this reply:

[COLOR="Red"]bash: Acquire::http::Proxy: command not found[/COLOR]

Something tells me something is not right here.....!?!

:-k Robin

---

### Post by robinduncan on 2006-10-17
ok, i guess - after more research - that the reason i can't install the flash plugin is because of something to do with "ppc architecture" Great!:neutral: 

Can anyonone recommend or de-recommend Gnash? I downloaded it, but am not sure how to install it.

any advice, commiserations etc. welcome.
later;) ,
robin

---

### Post by @stro on 2006-10-17
```
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
```
Why I am getting this error? :confused:

---

### Post by rlozano on 2006-10-18
double check though... it seems to be not working with the edgy stuff...

---

### Post by RudolfMDLT on 2006-10-18
robinduncan,

We seriously have to work on our comminication skills! ;) 
>  Acquire::http::Proxy "false";

The above is the contents of my /etc/apt/apt.conf file. (not a command) please open  your apt.conf file and see if it looks like this. chances are that it doesn't.

open it with the following code

> sudo gedit /etc/apt/apt.conf

Save the file as something else as a backup(ie. apt.conf~ or apt.conf.back) and close the text editor. Reopen the original with the above command and erase the contents of this file. Copy and paste this into it:
> 
 Acquire::http::Proxy "false";

and save it. Retsart your machine and then repeat all the steps in post #46 of this thread. see if it works. if it doesn't please post all errors and exactly what you did. Don't say "I followed post#46", please specify details, "I entered [this command] and this error was produced". I know it sounds cumborsome but we are not understanding each other and it might help solving the problem at hand.
 

Goodluck,

Rudolf

---

### Post by Poliseno on 2006-10-18
I suggest VLC media player. It's the top !!!

---

### Post by robinduncan on 2006-10-18
> **RudolfMDLT said:**
> robinduncan,

We seriously have to work on our comminication skills! ;) 


The above is the contents of my /etc/apt/apt.conf file. (not a command) please open  your apt.conf file and see if it looks like this. chances are that it doesn't.



Hi Rudolf,
so, I copied the contents of your /etc/apt/apt.conf file ainto mine. I tried Synaptic, as you suggested, and sure enough, Automatix was there, and I installed it. i then tried to get Flash to install but it wouldn't. Following the adobe readme which comes with the download, I navigated to the directory and entered:

[COLOR="Red"]./flashplayer-installer[/COLOR]

I got the same message as before, ie:

[COLOR="Red"]Error: your architecture, \'ppc\', is not supported by the Macromedia Flash Player installer.[/COLOR]

I've found a thread elsewhere on this forum that explains that the Flash plugin does not work on the ppc linux architecture (I didn't install my Linux, the person who gave me the computer did - I suppose I have ppc Linux because I have a power mac, which use the power pc processer. So short of some other solution (such as gnash?) I guess I won't see any flash stuff.

On the other hand, I ran automatix afterwards, and it seemed to go ok. I honestly don't know if it installed everything properly yet (or even what most of those things are supposed to do).

Oh well, at least I'm learning...
thanks for your help Rudolf,
Robin:)

---

### Post by underdog512 on 2006-10-18
Is easy ubuntu going to work with edgy?  If I up grade from dapper to edgy will I need add or remove any codecs or anything like that?

---

### Post by JNasci7906 on 2006-10-18
hey yall thanks for this sticky its a great helps to all us new users....ok i have a specific question i hope can get answered...i have all the needed codecs and such, been using them fine for a few months without any problems...however, i have a movie in AVI format that when it plays looks like scrambled TV channels, the audio works fine and when i play it in firefox it plays the video fine(but the audio is delayed)...how can i fix this to play in mplayer or vlc or any of the other players??

thanks, Nash

---

### Post by Perfect Storm on 2006-10-18
Try remove totem plugin. That should do the tricks.

---

### Post by Alias- Human on 2006-10-18
I seam to get this every time I attempt to DL w32codecs;
> :~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I have redone my 'repositories' list (although mine stems from the US and not 'NZ'.... does that make a differance?). 

This same message comes up for 'libdvdcss2' and that is a very frustrating thing. If I have it corectly that is the library that is needed to play DVD's in my DVDrom that I bought based on its advertising that said it "Played DVD's". Right now it is about as worthwhile as a generic toaster that will only toast in a specific designers kitchen. 

Is there anything I can do?
Thanks for listening.

---

### Post by dnyhan on 2006-10-19
Just wanted to say nice forum, and thanks for the EasyUbuntu app.
People wonder why the uptake to Linux is so slow, for me its totally obvious - its a mess and very difficult to use.
I used it all through University and I detested it.

I don't have the time to figure out all these different little configurations and more importantly, I don't NEED to know.
Until I found that EasyUbuntu app, I was about to format the second HD.
Now I'm starting to enjoy it and gaining a little interest in it.

---

### Post by Shooree on 2006-10-19
Heya guys,

Great atmosphere on these forums and a great deal of stuff to learn! Anyhow, just a simple yes/no question from nooby young me:

Obviously, I just switched from M$. Now, due to the fact that I haven't got an internet connection on my Ubuntu 6.06 laptop, I'm wondering whether it's possible to download these thingies for playing multimedia, using windows and then transferring them to the laptop via usb or whatever. If it is, please advise on the procedure. Or do I have to go buy a wireless? I mean, I -will- buy it at some point, it's just that I'm trying not to spend money if it isn't completely necessary. Hope you understand.

Many thanks and keep up the great work. Can't wait to get involved.

---

### Post by Perfect Storm on 2006-10-19
You can download the .deb package and eg. burn them to a CD. Just make sure you'll get the dependency packages with them.

a good place to seek for packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by rowster27 on 2006-10-19
hey guys why don't you try "afterbirth" by dyssident its kinda new and i like his idea checkout this thread [http://ubuntuforums.org/showthread.php?t=257116&highlight=afterbirth](http://ubuntuforums.org/showthread.php?t=257116&highlight=afterbirth)

thank you ubuntu and God bless to you all..

---

### Post by sean blah blah blah on 2006-10-19
nice ideas but im having problems with easy ubuntu...
any suggestions?

---

### Post by RudolfMDLT on 2006-10-19
Hi [COLOR="Blue"]sean,[/COLOR]

What troubles are you having? Or just install Automatix. On this thread a couple of people have had troubles with EU.


[COLOR="blue"]Alias- Human[/COLOR],

As far as I know it can ONLY be your repositories. Please browse through this thread and find the repository that I posted, i think it's on page 2. Verify that yours looks exactly like mine, it may have more entries but not less.
[COLOR="blue"]
underdog512[/COLOR],

All EU does is download stuff. If on edgy certain drivers are "core"(anybody feel free to correct my terminology please! :) ) dependant then I would suggest doing things manually through syanptic. Check out easyubuntu.org and see if it does support it.

[COLOR="blue"]robinduncan[/COLOR],

Sorry I'm getting to you last! :) PPC, thats interesting. I'm really sorry that flash won't wotk on that specific architecture. I know ZIP about Mac hardware, I'm sorry. I would suggest start a new thread with youre hardware details and config data and see if some one can help you!

Anyway,

Cheers

Rudolf

---

### Post by Shooree on 2006-10-19
> **Artificial Intelligence said:**
> You can download the .deb package and eg. burn them to a CD. Just make sure you'll get the dependency packages with them.

a good place to seek for packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Hi and thanks for the reply!
Just to clarify: packages.ubuntu.com has 3 categories of relatedness to the chosen package. Am I supposed to have all the red, i.e. those marked as "depends", packages installed as well, in order to get the desired app to work? And if I do, isn't there a more convenient way to get all the dependencies than to click them manually?

---

### Post by diggs on 2006-10-19
I think that you guys need to take a step back and say
"why in the hell is it so freaking hard to play a goddamn MP3 file in my poo brown operating system?"

and go from there

---

### Post by RudolfMDLT on 2006-10-19
> **diggs said:**
> I think that you guys need to take a step back and say
"why in the hell is it so freaking hard to play a goddamn MP3 file in my poo brown operating system?"

and go from there

Dear Mr. Diggs,

If you where trying to be funny you have succeeded! :D

---

### Post by Alias- Human on 2006-10-19
**Rudolf**, I tried as you said with the exact list you provided to DL 'w32codecs' and 'libdvdcss2'. When I refreshed my apt-get this is what I got at the end of it;

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done

Then as I tried to DL those two packages I once again got;

> :~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


I did manage to get Automatics2 DL'ed, so that is progress :) . Is there another way to get those two packages? Or, get my comp to recognise that repository?

Thanks

---

### Post by Peter41az on 2006-10-19
> **diggs said:**
> I think that you guys need to take a step back and say
"why in the hell is it so freaking hard to play a goddamn MP3 file in my poo brown operating system?"

and go from there
second that. i remember the first time i ever tried to load VLC on mandrake. I thought a tarball was what i found under my truck :)

---

### Post by blendmaster on 2006-10-19
> Originally Posted by diggs View Post
I think that you guys need to take a step back and say
"why in the hell is it so freaking hard to play a goddamn MP3 file in my poo brown operating system?"

and go from there

Wow, answering that is easy!

The mp3 file extension, in and of itself, is legally owned by someone. Ubuntu, in and of itself, is legally owned by **no one**. That being said, if you were to try to produce an entirely open source OS, you can't use copyrighted stuff!

That's why mp3 isn't supported on base installs, and it's probably for the best, as most people into linux, are looking for a way out of all those licenses and copyrights.

However, this doesn't apply to most people. A lot of people still like to play their songs that they purchased (hopefully purchased), because they bought it and should be able to play it. That's what this thread is for. It shows simple ways to install support for these licensed formats, in ways that pretty much anyone could do.

If you are asking this question in the first place, you probably shouldn't be using ubuntu and should go back to Windows, where everything is preinstalled, but because you paid a lot of money for it.

---

### Post by Alias- Human on 2006-10-19
](*,)  Well, I have an answer to my portion of this problem about w32codecs and libdvdcss2;

I live in the USA.
 At the beginning of Automatix2 it explains that it is illegal for people in the United States to DL those two things without paying a fee for their use. It Does Not say where one might pay such a fee. It does Not address the fact that anybody that has bought a DVD player/ROM for their computer has Already Payed such a fee For Its Use In Playing DVDs, VCDs, etc, AND Pays for such use again Each Time they buy a DVD or other rights protected stuff.

I bought a [COLOR="Red"]'Samsung CD-RW plus DVD ROM'[/COLOR] drive for my computer. It was sold to me as a piece of equipment that would "play DVD's".
Buying my use of the codecs and software to play those DVD's was part of the purchase price that I payed.

What I was NOT told was that this was true,
Apparently, Only If I Also Payed Microsoft and others a SECOND TIME for the use of my DVD player.

Does anybody know where we in the USA might find the selfish double/triple charging bastards that own the rights to these things so that we can pay them AGAIN for the use of Our legaly purchased equipment and DVDs?
(Or, so we can take them to court, again, for gouging us so badly).

---

### Post by bdb on 2006-10-19
I too have downloaded all the correct codecs etc.  However, some programs, totem for instance, still don't play some music or videos correctly.  

In this case download VLC media player.  Instructions here:[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

If VLC still cannot play your file........

---

### Post by bdb on 2006-10-19
> **diggs said:**
> I think that you guys need to take a step back and say
"why in the hell is it so freaking hard to play a goddamn MP3 file in my poo brown operating system?"

and go from there
*steps back   *
 why in the hell is it so freaking hard to play a goddamn MP3 file in my poo brown operating system?

Why was I saying this again :0

---

### Post by RudolfMDLT on 2006-10-20
Hi guys,
Alias- Human,

You don't have to pay any one, well you do, but you don't...:confused:  trust me.

I really don't know what is up with your APT. please post your sources list.  

OR if you wish you could start another thread because this is going beyond my knowladge, unless some one else could chip in some advice! :)

Cheers,

Rudolf

PS:
[http://packages.ubuntu.com/dapper/graphics/mplayer](http://packages.ubuntu.com/dapper/graphics/mplayer)

If you check above and scroll right to the bottom you'll see that w32codecs are not avaliable.... very odd, can some one please explain?

---

### Post by jhenager on 2006-10-20
Here's what I am getting:
jeff@jeff-desktop:~$ sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jeff@jeff-desktop:~$ sudo apt-get install mplayer-skins
Reading package lists... Done
Building dependency tree... Done
mplayer-skins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jeff@jeff-desktop:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jeff@jeff-desktop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
********************************************************************
Most of the multimedia I have tried works ok, but no dvds, and no WMA files off of atlantafalcons.com, which is an issue.
I hate booting into Winders just to watch clips of my team.
Thanks in advance.

---

### Post by Perfect Storm on 2006-10-20
[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

add this to your sourcelist.

---

### Post by joshgtv6 on 2006-10-21
As I got the same response about the w32codecs package.  

jpeifley@jpeifley-desktop:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
jpeifley@jpeifley-desktop:~$


I really wanted to play mp3's so I kept reading like a good little newb and decided to give the Amarok player a shot.  Now i can play my mp3's.  I had also downloaded the WINE package so i'm not sure if you need them both to play mp3's.  Hope this helps someone and maybe somebody can shed some light on the issue trying to get the w32codecs installed.

---

### Post by Artemis3 on 2006-10-21
mp3 goes like this... Thomson owns the patent for the file format, there is a fee for decoders and another for encoders, either you pay a very expensive anual fee for unlimited copies or you pay for each copy. This of course only applies to certain countries. This could be paid either by the distribution or left to the individual user. Some countries even forbid distributing the binaries.

USA is the worst and they try to force the rest of the world to adopt similar laws, to various degrees of success. If you live in the USA you are already guilty of something anyway and the best you can do is try to remain low profile (ie. don't talk about it).

Now with each of the other codecs there is a simillar situation, mp4 is owned by various corporations, for instance, and in some cases they simply forbid "others" not in their group from using their format.

So in short, the answer is: Patents.

---

### Post by RudolfMDLT on 2006-10-22
Artemis3,

Thanks for the explanation, I thought mo3 was owned by Dolby, but there you go, thanks!

joshgtv6,

Amarok probally had the w32codecs as a dependancie and then it got downloaded. if you want to make sure your setup is fine please post your sources.list file.

sudo gedit /etc/apt/sources.list 

copy and paste the contents of the above file in a post and I'll check it for errors. If you don't paste it I cannot help you.

Thanks,

Rudolf

---

### Post by joshgtv6 on 2006-10-22
> **RudolfMDLT said:**
> Artemis3,

Thanks for the explanation, I thought mo3 was owned by Dolby, but there you go, thanks!

joshgtv6,

Amarok probally had the w32codecs as a dependancie and then it got downloaded. if you want to make sure your setup is fine please post your sources.list file.

sudo gedit /etc/apt/sources.list 

copy and paste the contents of the above file in a post and I'll check it for errors. If you don't paste it I cannot help you.

Thanks,

Rudolf

well everything is working and I eventually got the w32codec package to download but with a different command than the one in this thread but for the life of me i can't remember what it was.  I read it somewhere else and gave it a shot.  But here is my source list and thanks for giving me a hand.  

EDIT:  I remembered where I eventually got the w32codec package to install from because for some reason like i said it wouldn't work through terminal.  I actually ended up getting it installed through synaptic


> 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


---

### Post by RudolfMDLT on 2006-10-22
Hi there,

So you did get it working in Synaptic..... Thats very odd because all synaptic does is add the packadge that you tick in front of "sudo apt-get install ***" and then runs it as a script(as far as I know) so if synaptic could get it you should have been able to get it to.:confused: 

Anyhow I'm glad that it's working.

Your sources list seems fine - You might need to uncomment the backports but if your system is fine then you can just as well leave them.

Cheers,

Rudolf

---

### Post by Alias- Human on 2006-10-22
**RudolfMDLT**; 
I tried simply replacing my source.list with yours by using "sudo gedit /etc/apt/sources.list" and still got those error messages. 
on occasion (when refreshing source.list) mine said something about .gz being different than it knew how to deal with.
> Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) [COLOR="Red"]Sub-process gzip returned an error code (1)[/COLOR]
here is my curent source.list, (I added all the other stuff to my original After trying your list by it's self);
> deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper main restricted
# # Major bug fix updates produced after the final release of the
# # distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# # Uncomment the following two lines to add software from the universe
# # repository.
# # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# # team, and may not be under a free licence. Please satisfy yourself as to
# # your rights to use the software. Also, please note that software in
# # universe WILL NOT receive any review or updates from the Ubuntu security
# # team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper universe
# # Uncomment the following two lines to add software from the backports
# # repository.
# # N.B. software from this repository may not have been tested as
# # extensively as that contained in the main release, although it includes
# # newer versions of some applications which may provide useful features.
# # Also, please note that software in backports WILL NOT receive any review
# # or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

I went to [VLC]("http://www.videolan.org/")'s web site and read their instruction and help pages and found this;
> The use and distribution of the libdvdcss library is controversial in a few countries such as the United States because of a law called the DMCA (Digital Millennium Copyright Act). If you are unsure about the legality of using and distributing this library in your country, please consult your lawyer.
Note

Beware: VLC media player binaries are distributed with the libdvdcss library included.
3.4.	

What about personal/commercial usage?
	

Some of the codecs distributed with VLC are patented and require you to pay royalties to their licensors. These are mostly the MPEG style codecs.

With many products the producer pays the license body (in this case MPEG LA) so the user (commercial or personal) does not have to take care of this. VLC (and ffmpeg and libmpeg2 which it uses in most of these cases) cannot do this because they are Free and Open Source implementations of these codecs. The software is not sold and therefore the end-user becomes responsible for complying to the licensing and royalty requirements. You will need to contact the licensor on how to comply to these licenses.

This goes for playing a DVD with VLC for your personal joy ($2.50 one time payment to MPEG LA) as well as for using VLC for streaming a live event in MPEG-4 over the Internet. 

I then went to the MPEG LA website and spent an hour or so reading about how they represent all the various patent and copyright holders of these codecs. 
So I sent them an E-MAIL asking for a solution/price-to-use/how to -install-on-linux and mildly described the frustration we all are experiencing, 
(I waited untill I had cooled down somewhat).
I don't expect a reply untill Monday at the earliest.

I'll post what ever they tell me, when and if they do tell me anything.
A H Dan R L0w {Low}

---

### Post by joshgtv6 on 2006-10-22
> **RudolfMDLT said:**
> Hi there,

So you did get it working in Synaptic..... Thats very odd because all synaptic does is add the packadge that you tick in front of "sudo apt-get install ***" and then runs it as a script(as far as I know) so if synaptic could get it you should have been able to get it to.:confused: 

Anyhow I'm glad that it's working.

Your sources list seems fine - You might need to uncomment the backports but if your system is fine then you can just as well leave them.

Cheers,

Rudolf

i know, i was equally confused but I just kept my cool and continued to try different things.  Now i have my system up and running with everything I wanted it to have minus the shockwave plugins which I already now how to get to work if I can't live without it.  Still debating if I want to use my second hardrive for a Windows install to run my games.

---

### Post by RudolfMDLT on 2006-10-23
Hi there

Alias- Human,

Okay, you're running both the ZA(South African) and the US repositories. I really don't know what effect that would have on APT. sorry. This is getting dragged out and must be frustrating you. Please post the entire output sothat I can see the packdge being downloaded, where it's comming from and then maybe read something out of it.

joshgtv6,

If you have a windows copy i would suggest installing it. I really like Ubuntu but for games, the just work in windows. But before you decide checkout this post:
[http://ubuntuforums.org/showthread.php?p=1589514#post1589514](http://ubuntuforums.org/showthread.php?p=1589514#post1589514)

Cheers,

Rudolf

---

### Post by Tobster on 2006-10-25
The Automatix stuff and Easy Ubuntu take a while to work out just remember that you copy and paste the codec for Easy Ubuntu

Press Enter - then WAIT for it to down load then;

Type in your password the one you use to log in but:

NOTING WILL HAPPEN but as you type in your password it is being inputted 

press ENTER

then it will download.  Called me stupid but the above is were I kept going wrong.

To get all your DVD's working also download Xine Movie Player from Synpatic Package Manager  Xine as extra codec and quick time.

To be really cool you can watch ABC News on Ubuntu by downloading Democracy Internet TV player Automatix then download the ABC feed.  Automatix works like Easy Ubuntu.

Have fun

Toby

---

### Post by Abhi Kalyan on 2006-10-25
Hi AI,
Thank a tonne for the help you nad forum had given me couple of days back.
I came here cause i was having problems with using media files.
Getting loads of stuff cleared.
Thank You guys.
Gonna Tryout Automatix currently.
Sincerely
Abhi Kalyan - (Am a noob )

---

### Post by Abhi Kalyan on 2006-10-25
Hi Artificaial Intellegance,
Thank you for the help you had given some time back.
Just now installed Automatix- Great Piece.
Thank you and every one in this forum.

---

### Post by Perfect Storm on 2006-10-25
The pleasure is mine :)

---

### Post by Abhi Kalyan on 2006-10-26
Me gotta doubt: couple actually :
1. Is it possible to make synaptic search for these packages in the CD's/ locations where we might store these packages?
2. Is it alright to download them to some location ad directly burn them?
3. Is it necessary to save them in certain formats to let synaptic find them?

Thank you once again.

---

### Post by RudolfMDLT on 2006-10-26
1.What you can do is search the cd for the packadge you want to install, ie w32codecs. It should be in the form of a deb file. When you do find it you can just double click it and the new dep file manager in Dapper should take over and install it.
                                 or
If you're looking for a way to backup your archives, the folder "/var/cache/apt/archives/" contains them all. Whatever you want to add and let synaptic find you can just copy and past iin said folder.
                                 or
In synaptic under settings=>repositories you can click "CDROM" inorder to use packadges on a cd-rom.


2.Yes

3.Yes, most importantly whatever you download must be a *.deb file inorder for synaptic or an archive manager to use them. If you download source then you have to compile it(if you're interested say so:) ). inorder for synaptic to use them. copy and paste the file in the above folder directly.

Hope this helps,

Cheers!

---

### Post by Abhi Kalyan on 2006-10-26
Thank you RudolfMDLT,
3. Yes am interested to learn how to compile, what i download.
Thank you RudolfMDLT, nice of you for asking if am interested.
Thank you

---

### Post by RudolfMDLT on 2006-10-26
Well, in principle compiling from source is a lot easier than it sounds. You'll find some Linux apps on the web that are only available in RPM packages or source downloads. Ubuntu can't use RPM so you'll have to download the source code. Once you have downloaded the source, uncompress the contents into a folder. then open up the terminal and set your working directory to the folder in which the uncompressed files are.

“cd /home/desktop/newapp”

then enter the following three commands.

sh configure

sudo make

sudo make install

This should work. But as always you may need some extra files installed on your system. one package you'll definitely need before you can start compiling stuff from source is build-essential 


sudo apt-get install build-essential 

Hope this gets you started. If you do get stuck start a new thread because my knowledge on compiling from source is very limited!:) 

Cheers!

Rudolf

---

### Post by Perfect Storm on 2006-10-26
Compiling is a bit tricky sometimes, it really depends which and how the maker of the application/libs/etc. have set up the source and which application he used for it.
The best way is to read the readme.txt that sometimes folloes the source and/or read more about it on their homepage.

---

### Post by RudolfMDLT on 2006-10-26
Abhi Kalyan, listen too what the polar bear said! :) Thanks AI, I've only ever had Kopete compile perfectly! every thing else needed tweaking of some kind.

---

### Post by Takmadeus on 2006-10-26
I have had to compile a lot of things isince i am using linux (like 8 years up to now).... and every package has its tricks and needs.... my advice is to download the source of what you want, do a ./configure --help and activate all those options that are hidden but may boost that package (works like a charm in gaim :p) and when it configures keep an eye on what it says that is not present, and as soon as you see it is a package, do a quick search in google or freshmeat for it and proceed to install it...... once the original ./configure says everything is OK and present, then you can rest assured that your package is going to compile perfectly, and will run smoothly and nicely ;)

---

### Post by ardvark71 on 2006-10-27
Hi all...

Is there a way to get past this:

Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package w32codecs has no installation candidate

Sorry.......I'm a little new to all this

Thanks!

---

### Post by RudolfMDLT on 2006-10-27
Hi!

Read the first post and make sure that your sources list is setup correctly. Then, in synaptic, click on mark all updates. and click apply. after this, search for w32condecs in synaptic and you can then click and download it.

Cheers,

Rudolf

---

### Post by Abhi Kalyan on 2006-10-27
Thank you  RudolfMDLT
When i type the command
"sudo apt-get install build-essentials"
I get the following message
"abhi is not in the sudoers file.  This incident will be reported."
I have root priviledge as i had installed and am running this system till date.
What could be the problem?
I recently went on a installation frenzy and installed LOADS of stuff.
I seriously dont rememebr what all i installed.
But my Applications menus is loaded Really Heavly.
And when i try to unistalla something It just doesnt happen.
It i need to edit sudoers list, then i will do it, But can you help me by pointing on how and why am getting thi message?

Thank you RudolfMDLT Once again.

---

### Post by Abhi Kalyan on 2006-10-27
will make a point to read the readme, when i complile any programs,
Thank you AI, That swell.

---

### Post by Abhi Kalyan on 2006-10-27
Thank you Takmadeus,
Am taking notes of all this information,
Thank you - Will procede with caution.

---

### Post by RudolfMDLT on 2006-10-27
Hi abhi,

Sorry I can't filter this for you to find what you need. I'm writing my final exams. 

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo#_Toc92808557](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo#_Toc92808557)

Hope this helps!

---

### Post by Abhi Kalyan on 2006-10-27
RudolfMDLT, Thank you 
And All the best,
Please do post on the after the exams,
Do well.

---

### Post by RudolfMDLT on 2006-10-27
I'll be posting straight through the exams! :)  I almost failed in June because of Ubuntu! It really is the most addictive thing around!:-D

---

### Post by ardvark71 on 2006-10-27
Hi Rudolf...

Was your post after mine meant for me or for the other person?

If so, What do I edit in the sources list and how?

Thanks!

---

### Post by ardvark71 on 2006-10-27
Hi Rudolf...

Nevermind....issue solved:-D

---

### Post by Abhi Kalyan on 2006-10-28
Sure RudolfMDLT,
" you score yourself from what you are capable of, the other score from what you have done "
The world is primitive and has forgotton curiocity.
All the best buddy,
God go with you. Cheers!!

---

### Post by tk92 on 2006-10-28
Thanks for this Very Outstanding information.

---

### Post by RudolfMDLT on 2006-10-28
tk92 - My pleasure man! Glad it got you sorted!:mrgreen:

---

### Post by Martin1 on 2006-10-29
I use Audacity to convert mp3 or other copywrited files to wav files this seems to work.

---

### Post by RudolfMDLT on 2006-10-29
That will work except thats undoing the entire purpose of a mp3! If you really want to be legal and have terabytes of space, sure, go  for it. I need the mp3 codec because I have 4000 mp3's on my sytem on avarage 7 megs/file. Thats 28Gb of music. Using wav I'll need 280Gb of space for the smae amount of music and quality.

---

### Post by Perfect Storm on 2006-10-29
What about converting it to .ogg instead?

---

### Post by Takmadeus on 2006-10-29
correct, but there is a problem (happens to me most of the time) and is that my mp3 player does not support ogg files (I wish it did) so some of us got to stick to mp3 :(

---

### Post by RudolfMDLT on 2006-10-30
Is converting to mp3 really such a problem? It's not open source, but it's not like you need a serial key generator or a crack every time you need to encode something.

---

### Post by b1g4L on 2006-10-30
Easy Ubuntu is reachable now. You can update the original post.

---

### Post by RudolfMDLT on 2006-10-31
b1g4L,

Thanks! I really appreciate you telling me! Awesome! I'll update now!

Cheers,

Rudolf

---

### Post by Takmadeus on 2006-10-31
That's quite correct, yet there is people that thinks that everything must be open sourced (which is respectable) yet I think I should use what I need, and if I need mp3, then I'll use mp3, plus, all my music is already in that format so I think there is no need to change it ;)

---

### Post by RudolfMDLT on 2006-10-31
i agree fully. :)

---

### Post by muggins on 2006-10-31
> **Artificial Intelligence said:**
> What about converting it to .ogg instead?

How would I or what do I use to convert to .ogg?

---

### Post by RudolfMDLT on 2006-10-31
check out this post:

[http://ubuntuforums.org/showthread.php?t=54635&highlight=Converting+ogg](http://ubuntuforums.org/showthread.php?t=54635&highlight=Converting+ogg)

Cheers!

---

### Post by __InFeRnO__ on 2006-11-01
So I used Automatix and it really screwd something up lol. I cant use the update manager anymore.

[http://img.photobucket.com/albums/v290/STInferno/Screenshot-2.png](http://img.photobucket.com/albums/v290/STInferno/Screenshot-2.png)

[http://img.photobucket.com/albums/v290/STInferno/Screenshot-1.png](http://img.photobucket.com/albums/v290/STInferno/Screenshot-1.png)

[http://img.photobucket.com/albums/v290/STInferno/Screenshot.png](http://img.photobucket.com/albums/v290/STInferno/Screenshot.png)

I got lots of errors and now and I need to know how to fix this.
How do I get superuser privileges ?

Any help with this would be awesome, thanks.

---

### Post by RudolfMDLT on 2006-11-02
yip! had that in Breezy! :)

Try this!

sudo dpkg --configure -a

then

sudo apt-get install -f

See if this helps! if any errors, post back! :)

Cheers!


PS:

Root = Super User

SUDO = Super User DO

Sudo is a command telling Linux to DO what ever follows sudo as root.

---

### Post by __InFeRnO__ on 2006-11-02
Problem solved. Man I'm lovin Ubuntu :D 

Thanks :smile:

---

### Post by RudolfMDLT on 2006-11-02
:)

---

### Post by ctopkelly on 2006-11-03
i had followed your direction and downloaded the easyubuntu app. it installs itself and every thing looks fine. i edit the sources.list file and i am good to go,  but when i try to open the easyunbuntu in the system tools menu nothing happens.

I still cant open the media files i want.

need some help please
Ctop

---

### Post by RudolfMDLT on 2006-11-03
Hi there,

Try running it from the terminal:

sudo easyubuntu

or if that doesn't work :

> sudo apt-get install gxine w32codecs flashplugin-nonfree mplayer mplayer-skins mozilla-mplayer libdvdcss2

Copy and past the entire top line into the terminal. It will install most codecs and there dependencies. Feel free to remove things you don't need right now like "flashplugin-nonfree" or can't download. the ones you DO need is w32codecs and libdvdcss2.

Hope this sorts you,

Cheers,

Rudolf

---

### Post by ctopkelly on 2006-11-03
nope i get this 

```
Unable to determine desktop environment, falling back to gksudo
python: can't open file './easyubuntu.in': [Errno 2] No such file or directory

```

and with the other one is i cant download the w23codecs
 Ctop

---

### Post by BKK on 2006-11-03
I get this message when I try to install libdvdcss2 and also win32codecs,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by imageburn on 2006-11-04
Try this, and add it to your sources:

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

The Euros might change their mind soon, so get it while you can.

---

### Post by juvu on 2006-11-04
> **imageburn said:**
> Try this, and add it to your sources:

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

The Euros might change their mind soon, so get it while you can.

thanks ,i can do it now
---------------------------------------------------------------
find a chinese solution? [http://www.trans2chinese.com](http://www.trans2chinese.com)

---

### Post by RudolfMDLT on 2006-11-04
Ctokelly,

Sorry for the late reply, I live on the other side of the earth! :) 

Okay, your problem seems non codec related, I think you got a system error and thats keeping you from downloading stuff wit the Sudo command. I really have know idea to start so lets see if you can actually use the sudo command.

> synaptic


entering the above command should start synaptic but with a dialog telling you that it's starting without certain privileges.

close synaptic and enter this command:
> gksudo synaptic

You should get prompted for a password in dialog form. If this works then the rest of the stuff should work to. If it does produce errors though then please post back.

If you can open synaptic with gksudo the search for w32codecs, tick the box and install them.

I'll be waiting for your reply,

Cheers,



Rudolf

---

### Post by sashi on 2006-11-05
hey there...firstly i m really really new to linux systems....i got so sick of my xp i just popped in my ubuntu install disk and installed ubuntu..now the problem is i got no sound and i coudl t play any music files or video file...some how after tinkering about and with help from this forum i managed to install the codecs...but i still can t play the song ...i tried to istall my driver cd and my vga card driver cd but i can t seem to get it to auto run...the codec i installed are vlc player codecs...i really stumped as what to do now...could some one please please help me:( ...other than that ubuntu seriously seriously rock big time:D thanks

---

### Post by RudolfMDLT on 2006-11-05
Hi sashi,

Okay, Intro To Linux: ;)

Windows executables(.exe files/programs written for windows) will only ever work in linux under special circumstances. Windows drivers WILL NEVER work in an linux environment. The reason is as follow; 

_____________________
Operating System     |
_____________________|
Driver/Interpreter  |
_____________________|
Hardware             |
_____________________|

The driver sits between the OS and the Hardware and translates between the two, a windows translator won't be able to talk to Ubuntu. I am not that up to scratch with trouble shooting sound-hardware in Linux but I doubt that you have hardware problems.

please copy and paste the following line into the terminal and press enter:

> sudo apt-get install gxine w32codecs flashplugin-nonfree mplayer mplayer-skins mozilla-mplayer libdvdcss2

This should sort out most problems. If it does not then Please post back so that we can take it further from there. Please tell me whether when you boot up Ubuntu you here the intro music or not, it's an African drum beat or something like that.


This is how linux software installations work:

There is a big pile of software on a server some where, you have an app called synaptic on your machine and a config file called sources. This app uses the config file to find these servers and then updates it's catalog of the software pile. Using Synaptic you can install software for free. 

Hope this helps get you started! Please post back with any errors and I'll try and help you.

Cheers,

Rudolf

---

### Post by shortsellyhoonow on 2006-11-05
can somebody tell me how to install gtkpod?

I can't even install it from source because this **** distro doesn't even have a C compiler!

---

### Post by jd65pl on 2006-11-05
> **shortsellyhoonow said:**
> can somebody tell me how to install gtkpod?

I can't even install it from source because this **** distro doesn't even have a C compiler!

A little rash personifying an operating system! Try searching for build essential for a C compiler

---

### Post by Peter41az on 2006-11-05
> **jd65pl said:**
> A little rash personifying an operating system! Try searching for build essential for a C compiler
lmao at personifying.

GCC isnt a C Compiler? sure looks like one to me.

---

### Post by jd65pl on 2006-11-05
>  this faggot distro

Adding human qualities to an inanimate object - personification (in english anyway) but thats by the by

---

### Post by RudolfMDLT on 2006-11-06
> **shortsellyhoonow said:**
> can somebody tell me how to install gtkpod?

I can't even install it from source because this ***** distro doesn't even have a C compiler!

Dude, this is my thread - Go **** distro some place else! No Ubuntu Bashing allowed! Critisism yes, but not that!

sudo apt-get install build-essential

You'll have everything you need.

EDIT: **** man - sudo apt-get install gtkpod

---

### Post by Abhi Kalyan on 2006-11-06
> **shortsellyhoonow said:**
> can somebody tell me how to install gtkpod?

I can't even install it from source because this **** distro doesn't even have a C compiler!
With all due respects Sir,
Please check out
1. the " UBUNTU code of conduct"
2. The sticky posts way above on the screen in the forum entry point.
3. This is a great place to be, and some politeness can get you real far
4. You get to meet and know lots of people, and loads of information

Example: I started out with Linux/Ubuntu coupld of days back and now am feeling a lot more comfortable with linux than with windoes, I have been windowing for almost eight years.

Hoping to see you here clearing your doubts and also helping others with knowledge that you already have.

You are good and you have a purpose, Try finding it out we are all one for all and all for one.
Please do not get offended, cause we all slip before we slide.

SLIDE!!!
Cheers
Sincerely
Abhi Kalyan

---

### Post by kaemrhynn on 2006-11-06
Hey all, I am having difficulties installing w32codecs.  I am running Xubuntu 6.10 Edgy Eft on a Celeron 533 with 128MB RAM, primarily used for word-processing, net surfing and as a jukebox.

From the terminal I type in:

```
sudo apt-get install w32codecs
```

and get the following message:

> case@Flatline:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
case@Flatline:~$ 


I have tried adding the repository suggested by imageburn:

> **imageburn said:**
> Try this, and add it to your sources:

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

The Euros might change their mind soon, so get it while you can.

But I get the same message.  So if anyone has any suggestions, I would be most grateful.


EDIT: Got it sorted, forgot to do ```
sudo apt-get update
``` lol :)

---

### Post by RudolfMDLT on 2006-11-06
Glad you got sorted mate! :)

---

### Post by sashi on 2006-11-06
hey Rudolf,
 thanks for the tip.. i entered the code you gave me in the terminal i got a reply saying the packet could t be found..and no i don t hear any sound when ubuntu loads..thanks for replying:) 

gratefully,
sashi

---

### Post by RudolfMDLT on 2006-11-06
Hi Sashi,

If you don't hear sound I think you have a hardware problem. To get the most attention it would be best that you start your own thread under Hardware and Laptops or Multimedia issues - There people who know how to fix sound issues will be able to help you. Unfortunatlu I really don't know where to start concerning you sound. To get the most help in your thread, specify your machine's hardware and confuguration and a bit more detail. 

Sorry Mate,

Cheers,

Rudolf

---

### Post by koo-koo on 2006-11-06
I'm having a few issues myself with codecs and multimedia.  I'm running Ubuntu 5.10 with a P4 1.3Ghz and 394MB of RAM.  I've downloaded most of the things this thread has recommended (vlc,w32codecs,libdvdcss,gxine,mplayer), and even a few other things(libmatroska,ffplay).  However, some problems have crept up...

*MP4 files play like crap, typically crashing after a few seconds in vlc (this doesn't happen in Windows - they play perfectly), or play such that video is several times slower than audio in mplayer.

*MKV files play like crap in vlc with some blur filling the screen.  In mplayer they work fine (or a tad slower then they should), but I can't figure out how to set up a font to get subtitles.  I have no idea where .ttf fonts are on the system or where to download any.

*WMV files are fine in gxine, but they crash mplayer such that it may be impossible to kill the process from System Monitor.  A shadow of the skin and controls will cover part of the wallpaper if the process cannot be killed without restarting.

I guess some of this may be due to low memory or my 64MB Nvidia card (3D screensavers seem to pause every few seconds), but I'm not so certain.  I've tried EasyUbuntu and Automatix, but I get some strange errors concerning wrong passwords or uninstallable packages, so I've given up on them.  Is there a freeware converter to change mp4 files into avi (or ogg), or a better player for linux than the ones already mentioned?  Or is it a matter of having to find better codecs?

---

### Post by Abhi Kalyan on 2006-11-06
Automatix has it all:
Please read above to get certaing repository addresses, whihc have what you might need.
The 3d functionality does lay heavy load on the Processor more than the Ram.
Please check the system status for understanding the issue.
It could also be driver problem with the onboard GFX card, This is somewhat away from a solid Ram problem.
If you are planning to upgrade please do try out the solutions with the current rig before you go digging for hardware, This is true for reasons more than one
Thank you Buddy
Happy hunting!

---

### Post by koo-koo on 2006-11-06
I've tried to install automatix2, but it depends on 'tango-icon-theme-common' and I can't find it.  I guess it's because I'm running 5.10 and this is made for 6.06 or 6.10.  I could try EasyUbuntu again, but I don't know if I want to go through that just to be told that I entered in the wrong password somewhere without knowing what the correct password is...

The screensavers work better now.  I forgot to mention that I was running BitTorrent 5.0 for quite a while and as soon as I quit, my CPU % dropped along with memory and swap.  Also, I'm not using an onboard GFX card - it's in the AGP slot.

---

### Post by Takmadeus on 2006-11-06
Greetings again.... I just wanted to remind any of you who is willing to help me that I opened a thread to discuss jumpy xine issues.... thanks

[http://www.ubuntuforums.org/showthread.php?t=287504](http://www.ubuntuforums.org/showthread.php?t=287504)

I hope we get a good discussion plus a solution for this annoying problem :)

---

### Post by Orwell on 2006-11-07
Thanks heaps for the info. Having never used a Linux OS before, I was a little dubious. Installed it last night, and thanks to posts like yours, I am now happily MS-free!

cheers!:KS

---

### Post by RudolfMDLT on 2006-11-07
Orwell, Big pleasure dude!

Hi Koo-Koo,

I'm a little lost here, are you running a new instillation of breezy Badger and you are a new user, or are you an old hat user running an older system?

Please post back with your system config, maybe you have an hardware(display) issue - though i doubt it? Though, some of your kit is a little old, it's still no excuse for not being able to play codecs.

---

### Post by koo-koo on 2006-11-07
RudolfMDLT:

Yes, I'm a new user.  New to Ubuntu, new to Linux on my desktop.  I run Breezy because neither Dapper nor Edgy seem to work with my wireless usb adapter, a US Robotics 5422 model.  I have a thread about this in the Networking forum - search under 'US robotics wireless usb adapter'.  If I could get a newer version to work with my wireless connection, I would have already upgraded.

My system is a Dell Dimension 8100 with P4 1.3Ghz, 20GB hdd, 384MB rdram, 64MB GeForce4 GFX card, 2 CD-RW drives, and a 40GB hdd that has Windows 2000.  

I played a MP4 file in Mplayer with near perfect results a few hours ago.  The catch - I had upgraded XFree86 to 4.6.0 and this does two things.  One, it blocks out the 1280x1024 resolution on my video card (11** max), and two, there seems to be a 'bleeding' effect whenever I highlight a region on the background, drag a window around, or minimize a window.

It's not that codecs don't play at all.  Usually, MP4 video either runs at 30 FPS while sound runs normally, or MP4 video has annoying blur if it runs at the same rate as the sound.  AVI files are fine, and so are MPG/WMV.  MKV files seem to have the same issues as MP4 video, plus the added frustration of not being able to find a proper font to display the subtitles in.  The font provided by vlc (at least I think it's included) is too big.

---

### Post by RudolfMDLT on 2006-11-07
See if this helps?

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

I don't think this is free - but give it a read...

---

### Post by koo-koo on 2006-11-07
I guess it is free, since I wasn't prompted to pay or register (yet?).  I just downloaded a .deb package onto a floppy disk for the newest version of the kernel, so now I can retry installation from my Kubuntu Edgy disk.  If that doesn't work, I'll try reinstalling Ubuntu Dapper with the package that matches its kernel.

---

### Post by RudolfMDLT on 2006-11-08
Well, I really hope it works! Goodluck! :)

---

### Post by koo-koo on 2006-11-08
I reinstalled Kubuntu Edgy and set up driverloader.  One thing I noticed right away was that instead of my wireless adapter's light always being on, it was only on when trying to connect.  Iwconfig also reports the interface as wlan0 instead of eth0 while driverloader is set up.  

Unfortunately, my signal quality dropped to ridiculously low levels and I still couldn't connect to an access point (though I also didn't want to bother with giving out lots of personal information just for a free trial or paying $20 for a permanent license).

I'm still wondering how Ubuntu Breezy could work with ndiswrapper and yet neither Dapper nor Edgy can.  I think Breezy reporting my interface as wlan0 and the others as eth0 has much to do with it.  Maybe it's a problem related to USB detection?

I tried upgrading Breezy to Dapper through the Update Manager gui and after the installation, my internet still worked.  This was until I restarted the system and then my internet died regardless of which kernel version I booted up from (2.6.12 or 2.6.15).

At this point, I think I'm going to install Breezy again and try installing a different version of XFree86 other than the newest.  Maybe that will help...

---

### Post by RudolfMDLT on 2006-11-08
Koo-koo, sorry to hear about that! It's odd that an upgraded OS doesn't support the older hardware. Sorry about that!

---

### Post by koo-koo on 2006-11-08
It's alright.  I'll eventually buy a networking device in the future that is sure to be Linux-compatible, along with some other hardware.  Breezy is back on my system now, and I've given up on trying to upgrade XFree86 on my own.  Too many strange things happen, such as my middle mouse button not scrolling, some programs in the menu not starting once clicked, and Xserver restarting 6 times per minute.

I'm glad to say that I've got MP4 files to work properly now.  I had to install the latest nightly build for vlc from nightlies.videolan.org and tweak some settings related to ffmpeg and h264 ("Skip loop filter for h264 encoding" to "All" & uncheck anything that takes extra CPU).  Whereas Mplayer would give near-perfect results, the tweaked vlc gives perfect results.  WMV and MPG are unaffected, making vlc the only player I need for just about every format I've come across.

Thanks for the help!

---

### Post by TheThirdGhost on 2006-11-09
very good thread:)

---

### Post by lord_Kalaeth on 2006-11-09
cant get the win32 codecs...
I run :  sudo apt-get install w32codecs
and I get this :
```

Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

I'm running Ubuntu 6.10, and I've got restricted, multiverse & universe in my source list.. I even tried to change my source list to [this one]("http://ubuntuforums.org/showpost.php?p=1619671&postcount=29") but I allways get the same msg....

---

### Post by RudolfMDLT on 2006-11-10
Hi people!

Koo-koo,

Sorry I'm only posting now, Exams are the Devil! :) Anyway, I'm really glad you got it working and I'll make a mental note for older machines! with XFree86, dod you try and ask for help on the forum? :)  Anyway, glad your codec issues where sorted!

TheThirdGohst,

Thanks! :D 

lord_Kalaeth,

Your using my clean one...Thats odd...:-k  

OOOOOO!! Damn - you had me going on this one for about 10 min now! Those are Dapper packages! not Edgy! :mrgreen: It had me fooled too! sorry, the lady that needed them was using dapper. I'm sorry about that!

Here you go, this one will sort you out:
[PHP]

deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
# # Major bug fix updates produced after the final release of the
# # distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
# # Uncomment the following two lines to add software from the  universe
# # repository.
# # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# # team, and may not be under a free licence. Please satisfy yourself as to
# # your rights to use the software. Also, please note that software in
# # universe WILL NOT receive any review or updates from the Ubuntu security
# # team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
# # Uncomment the following two lines to add software from the  backports
# # repository.
# # N.B. software from this repository may not have been tested as
# # extensively as that contained in the main release, although it includes
# # newer versions of some applications which may provide useful features.
# # Also, please note that software in backports WILL NOT receive any review
# # or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu/ edgy-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ edgy main

[/PHP]

I live in South Africa, so my list had za.something in, I changed the za to us and that should work, if it doesn't post back and I'll try and get you a clean one, look around in the /etc/apt folder, there should be a clean original lying around!

Best of luck,

Cheers,

Rudolf

---

### Post by Phalangees on 2006-12-01
Hi. Sorry if this is in the wrong place. I installed everything and mp3's work fine if they are saved locally on the hard drive but I can't play any music over the network where all my music is. All the music I want to access is on a windows computer and amarok will crash when I try to play them.

---

### Post by esaym on 2006-12-08
Why is this not stickied any more?

Anyway, I found a good "tester" page here: [http://gstreamer.freedesktop.org/media/](http://gstreamer.freedesktop.org/media/)

---

### Post by RudolfMDLT on 2006-12-10
Seeing as this is not stickied anymore can people please email me when you need help on this post because I don't check it everyday! Send me a PM by Clicking on the big Orange RudolfMDLT selecting - send this user a personal message.

Thanks,

Cheers!

---

### Post by hodad on 2006-12-17
OK, here's a VERY basic noobie question:

How does one go about buying and downloading music under Ubuntu?  I've never done this, and I've just gotten my first MP3 player.  All of the websites I've seen seem to cater only to windows or Mac.  Does anyone know of a good site (lots of music) where I can buy songs and actually download them to my Ubuntu machine (then load them into my player).  Is there an application somewhere in Ubuntu that can access these MP3 music sites?
Thanks in advance!!

---

### Post by Get_Ya_Wicked_On on 2006-12-17
[http://www.mininova.org](http://www.mininova.org)

[http://www.isohunt.com](http://www.isohunt.com)

etc, etc...

---

### Post by RudolfMDLT on 2006-12-19
you can find certain free mp3 sites - [www.emp3finder.com](www.emp3finder.com)

I use a pay site - [www.gomusic.ru](www.gomusic.ru)

---

### Post by hodad on 2006-12-19
Thanks for the sites, I'll check them out!

---

### Post by yuanfangcan on 2006-12-25
> **RudolfMDLT said:**
>  
[COLOR="Blue"]
 
Then a good media player, Amarok:
sudo apt-get install amarok
   
 

Thanks man. Amarok is really nice ! I can play wma file now

---

### Post by RudolfMDLT on 2006-12-25
> I got stuck trying to download Easyubuntu.

I have Dapper on my machine and here is the error I got:-

svn checkout svn://freecontrib.org/easyubuntu
svn: Berkeley DB error while opening 'nodes' table for filesystem /home/svn/repos/easyubuntu/db:
Cannot allocate memory
svn: bdb: Unable to allocate memory for transaction detail

My machine is a PC, Pent 4, 2.53GHz, 1GB RAM, 80GB hard drive and Dapper is the only thing on here.


Lewis.






Hi Lewis,

I don´t really know where to place the error as I don´t know how you installed it?

Anyway, you might then want to try AutoMatix? Some people have had some troubles with EU and then Automatix worked perfectly. There is very little difference in the end result when using either of the two.

If you could paste the entire terminal output that would be great as well, from the first command you entered to the final output. It seems as if you have typed the error out of the terminal. To copy and paste in the terminal you highlight the text and Ctrl+SHIFT+C. Some people sometimes miss the shift. 

Your machine is pretty high spec, shouldn´t be running out of memory. Firstly try restarting it and then redownload and install. Secondly if you´re worried, open up the terminal and type ¨top¨.  press Ctrl+C to stop TOP and post the output of the first 5 lines, ie:

top - 00:25:20 up  4:54,  1 user,  load average: 0.11, 0.19, 0.12
Tasks: 120 total,   8 running, 109 sleeping,   0 stopped,   3 zombie
Cpu(s):  4.9%us,  3.6%sy,  0.0%ni, 87.8%id,  3.6%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   1034860k total,  1017952k used,    16908k free,    55644k buffers
Swap:        0k total,        0k used,        0k free,   714728k cached

If you still can´t install EU, please try Automatix. If you still want the error resolved, please paste as previously asked the entire error.


Best of luck,

Rudolf

---

### Post by L Campbell on 2006-12-25
> **RudolfMDLT said:**
> Hi Lewis,

I don´t really know where to place the error as I don´t know how you installed it?

Anyway, you might then want to try AutoMatix? Some people have had some troubles with EU and then Automatix worked perfectly. There is very little difference in the end result when using either of the two.

If you could paste the entire terminal output that would be great as well, from the first command you entered to the final output. It seems as if you have typed the error out of the terminal. To copy and paste in the terminal you highlight the text and Ctrl+SHIFT+C. Some people sometimes miss the shift. 

Your machine is pretty high spec, shouldn´t be running out of memory. Firstly try restarting it and then redownload and install. Secondly if you´re worried, open up the terminal and type ¨top¨.  press Ctrl+C to stop TOP and post the output of the first 5 lines, ie:

top - 00:25:20 up  4:54,  1 user,  load average: 0.11, 0.19, 0.12
Tasks: 120 total,   8 running, 109 sleeping,   0 stopped,   3 zombie
Cpu(s):  4.9%us,  3.6%sy,  0.0%ni, 87.8%id,  3.6%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   1034860k total,  1017952k used,    16908k free,    55644k buffers
Swap:        0k total,        0k used,        0k free,   714728k cached

If you still can´t install EU, please try Automatix. If you still want the error resolved, please paste as previously asked the entire error.


Best of luck,

Rudolf



Hi, Rudolf, thanks very much for taking the time to respond.

I'll be back at my home computer in the morning and will get to work on it.

Kind regards.

---

### Post by RudolfMDLT on 2006-12-26
No problem!

---

### Post by L Campbell on 2006-12-26
> **RudolfMDLT said:**
> No problem!


Hi, Rudolph, I seem to have made some progress.  EasyUbuntu is now installed on my machine and Gizmo ( [http://www.gizmoproject.com/index.html](http://www.gizmoproject.com/index.html) ) is working well.

I do not have any plugins, for whatever reason but I'm trying to work on that now.

Hope you are having a great day and are warmer than we are here in Texas.   :-)

Kind regards.

---

### Post by RudolfMDLT on 2006-12-27
Oi! 30 degrees celsuis! about 110 Fahrenheit! Whish it was cold, like in texas! I prefer winter to summer any day!

---

### Post by ashmew2 on 2006-12-28
HI , Thanks for the great how-to. But i was having one problem that even after enabling the repositories , when i tried to  sudo apt-get install w32codecs   , it said No Candidate Found for w32codecs and the package might have been deleted and stuff. So i looked through google for this and i ultimately found a working solution (Thanks to [www.debianadmin.com](www.debianadmin.com)) .If any1 is having a similar problem , I am pretty sure that the following commands will help you.
For installing w32codecs :

wget  http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
dpkg -i w32codecs_20060611-0.0_i386.deb

For installing libdvdcss (which is a highly portable library for accessing and unscrambling DVDs encrypted with the CSS system. It is part of the VideoLAN project and is used by VLC and all other open source DVD players such as Ogle, xine-based players and MPlayer.) You do :

wget http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0sarge0.0_i386.deb

dpkg -i libdvdcss2_1.2.9-0sarge0.0_i386.deb
Hope this helped :D

---

### Post by RudolfMDLT on 2007-01-08
I've heard this from a friend aswell. can anyvody tell me what the name of the New Candidate for w32codecs is?

Thanks,

Rudolf

---

### Post by sargosis on 2007-02-20
i've been trying to get .mp4 video files to work on my system, but i can't seem to findthe correct codec. i used to have a 64bit system, but i converted to 32 bit one because there was more support. anyone know off hand which codec or package i need to watch .mp4 movies?

---

### Post by RudolfMDLT on 2007-02-20
Hi - This thread hasn't been active for a while and probably needs an  update... :)

sudo apt-get install libmp4v2-0


This should sort you out - also, what player are you using? Amarok/VLC/Kaffine are recommended.


Cheers,

Rudolf

---

### Post by sargosis on 2007-02-21
apparently, i already had that package. sadly, i still can't open the mp4 movies
up until recently, totem, mplayer, and xine had all been working just fine for me, i was able to open just about anything until the switch. 

btw, thank you. i greatly appreciate the timely response :)

---

### Post by sargosis on 2007-02-21
hey, i managed to fix it and i figured i'd let everyone else know the solution. 

i simply switched from totem-gstreamer to totem-xine. i dont have any clue why or how it works, but for me, it did.

---

### Post by lunaz on 2007-02-23
edit: oops i meant to make a thread. :( reposted. i should not post while otw out o_o

---

### Post by Ek0nomik on 2007-02-24
Thanks!  The command did the trick.  I got the MP3 decoder working just great.

---

### Post by RudolfMDLT on 2007-02-24
Sweet!:popcorn:

---

### Post by Takmadeus on 2007-03-05
Well.... here's the deal.... I had to reinstall ubuntu and then I looked for the add/remove software in the gnome menu.... just installed the codec pack featured in the multimedia section and then everything was good to go.... videos of every kind play like a charm now ;)

---

### Post by RudolfMDLT on 2007-03-05
No there's a simple solution! I'll quote it up front!

---

### Post by one_ro on 2007-11-10
Hey big gurus,

I followed the thread and installed *every* possible codec, my MP4 file openes just fine but it does NOT play sound :(

VLC, Kaffeine, MPlayer all play without sound.
Perhaps there is something I'm missing, could you please advice?

Thanks in advance,
Adrian

---

### Post by RudolfMDLT on 2007-11-11
Hi there one_ro,

I wrote this back when the codecs where really hard to get hold of and you had to hunt down and install each one. It's a little out dated and Adamant1988 has written a much more up to date one. Please follow his steps here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

That should get you working, If you have followed his advice to the letter, and followed it again and you still have no sound - do you have sound at startup? do some files play and others not? Is the playback jerky or nothing at all?

But I really think Adamant1988's post will sort you out as this one is very old! ;)

Best of luck,

Rudolf

---

### Post by Perfect Storm on 2007-11-11
I'm closing this thread, as it's old and not "relevant" anymore. RudolfMDLT if you want it reopen just PM me.

---

