---
title: "Help me install MPlayer :("
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Zonkle on 2005-12-18
Hi,

After trying to get Multimedia working , I saw that the most favorite choice is MPlayer.

I downloaded it and its codecs ...... I tried to compile it ...messed up a little ... now I only have MPlayer works in the Terminal only :???:  I don't see it in the "Applications" ... I tried to play MP3 file and it worked :) ... so I think there is hope to stay with Ubuntu :) ..... I'm getting those moments were I think to just leave the whole thing ... but I keep on coming back and trying.

So now can I get MPlayer to have nice GUI and play movies?
It looks like I have the codecs in the right place .....

I'm not lazy ...but I have 9 hours work a day setting infront of screen all day ,,, when I come back home I just don't have the power to go through all the errors and READMES!

Please help me.

Thanks.

---

### Post by Perfect Storm on 2005-12-18
any errors when you start in the terminal?

```

gmplayer

```

Edit: You may try this guide: [http://doc.gwos.org/index.php/Mplayer_cvs](http://doc.gwos.org/index.php/Mplayer_cvs)

---

### Post by Zonkle on 2005-12-18
Wow that was ultra fast!!

When I try gmplayer I get:

bash: gmplayer: command not found

So ?

Man .... how can I like uninstall MPlayer ?? I want to start fresh .... I will just wait for Broadband man .... I'm bored .... all steps for always online schema.

I've just copied the codecs to /usr/lib/local/something/codecs ... and in the MPlayer source folder I did:
make
make install

How can I uninstall it ?

---

### Post by Perfect Storm on 2005-12-18
try with

```
whereis mplayer

```

---

### Post by Zonkle on 2005-12-18
It says:

mplayer: /usr/local/bin/mplayer /usr/local/etc/mplayer /usr/local/lib/mplayer

So I should delete of that ?

After I get the Multimedia ... I will start fighting with the USB MSI Bluetooth to work ...... ahhh .... I it will be easy.

Why installation in Linux can't be easier :(? Like one nice Setup.exe we used to use?
All of this compiling and headache ....

---

### Post by Perfect Storm on 2005-12-18
Well It's very easy to install you just have to know how :)

If you don't want to compile, then write

```

sudo apt-get install mplayer-386

```

---

### Post by Perfect Storm on 2005-12-18
```
 sudo gedit /etc/apt/sources.list

```
delete all of the text and add instead:

> deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


then, save it

```

sudo apt-get update
sudo apt-get install mplayer-386 w32codec libdvdcss2

```

---

### Post by Zonkle on 2005-12-18
Maybe easy for you! .... but for new users they have to learn a lot(how compilers works what does it need what libraries to have .. and all the stuff they doesn't need to know about) to know to install applications **without** having **Broadband**.

I gave up .... so just tell me please how to uninstall it ... and I will run the internet all the night to download MPlayer ,, and I hope it will works.BTW, how big is it?

I have to delete all of these folders to have clean installation?:
mplayer: /usr/local/bin/mplayer /usr/local/etc/mplayer /usr/local/lib/mplayer

Thanks a lot for your patiance :) .... I'm just a little frustrated,,,

---

### Post by Perfect Storm on 2005-12-18
sorry, It wasn't meant to sound that way, wrong smiley I guess.

```

cd /usr/local/bin/
sudo rm -r mplayer 
cd /usr/local/etc
sudo rm -r mplayer
cd /usr/local/lib
sudo rm -r mplayer

```

By the way, you don't need to compile to install on ubuntu. Ubuntu is debian based and have package to easy use.
If you look at **System** tab --> **Adminstration** ---> **Synaptic package manager** you'll find a massive of packages.

---

### Post by Zonkle on 2005-12-18
Thanks.

I have w32codecs and libdvdcss2 install as I can see them in the synaptic ...

So I think I will just do:

sudo apt-get update
sudo apt-get install mplayer-386

Can you please just tell me how to delete the old  installation I did ?

Thanks in advance.

---

### Post by Perfect Storm on 2005-12-18
Just described above ^^

---

### Post by Zonkle on 2005-12-18
Thanks for the steps :)

It looks like mplayer is gone .... because when I type whereis mplayer - it just says mplayer:

Does it need any configurations when it is installing ? I mean when I do:
sudo apt-get update
sudo apt-get install mplayer-386

Will it ask any questions during downloading?

Because I will leave the dialup internet working through the night ... and I just don't wanna waste time while it is just waiting all night for me to press "Y" :D
And how big is the installation? ..... I just have 40Kbps :)

Thanks for your help.

---

### Post by Perfect Storm on 2005-12-18
You only need to [Y] in the start if there some extra packages it needs, after that you can leave alone. It do all the job for you :D

Edit: MPlayer is around 4 mb download without extra

---

### Post by Zonkle on 2005-12-18
That's great thank you. 4 MB is pretty much small :D great news. Can auto disconnect after finishing :P ?

Man ... my internet has proxy .. in the adminstration i did put the proxy settings .... now when I try to apt-get update i get like :
zonkle@Zonkle-Desktop:~$ sudo apt-get update
0% [Connecting to dk.archive.ubuntu.com (82.211.81.182)] [Connecting t Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
  Could not connect to wine.sourceforge.net:80 (66.35.250.209), connection timed out
Err [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
  Could not connect to deb.opera.com:80 (193.69.116.32), connection timed outErr [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to de.archive.ubuntu.com:80 (141.76.2.3), connection timed out
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (70.84.217.98), connection timed out
Err [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
  Could not connect to people.ubuntu.com:80 (82.211.81.132), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
  Could not connect to packages.freecontrib.org:80 (213.251.190.135), connection timed out
0% [Connecting to dk.archive.ubuntu.com (82.211.81.151)] [Connecting to arch

What's wrong ?

---

### Post by Perfect Storm on 2005-12-18
HOw's your repository looks like?
```
 sudo gedit /etc/apt/sources.list

```

Is Synaptic Package manager open? If so close it first.


Edit: It could be the servers are busy??? Never had that kind of error

---

### Post by Zonkle on 2005-12-18
This is it:

 deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

I saw in the Synaptic preferences there is proxy option ... should i play with that and "Reload packages" ? ... i get lot of errors when i start synapatic .. i think that's because it didn't get the info about the new stuff ...

---

### Post by Perfect Storm on 2005-12-18
You could try fiddle with the options. Just remember the default options.

Aye, reload.

---

### Post by Zonkle on 2005-12-18
Thanks AI for everything :)

I changed the proxy settings in Synapatic(It looks like it doesn't take the enviromental settings) and it started downloading :) ... but I saw some "Failed" messages in the downloadind window .. but i left it working ,,, when i came back i saw a big list of apps :D .. with these little starts :D it looks nice ...... so should i worry about these failed messages ? .. i think one of them were trying to connecto skype page ... but i searched in synapatic for skype and it was there :)

One more thing please ...... can I start downloading packages and just pause to continue downloading later ? or I'm asking a lot :P?

Thanks a lot .. and I hope Synapatic will just solve everything for me :)

---

### Post by Perfect Storm on 2005-12-18
Don't worry about the skype. 


If some of the packages are downloaded as whole, you can continue with the other files later, by cancel the download Just proceed as you did in the first place (downloading mplayer).

The errors it depends what the errors says, if I may have a look :)

---

### Post by zolero on 2005-12-18
I suggest a better, and faster way to do this. Install'n try Arnieboy's Automatix 4 and all your problems going away...;) Here is the downloadlink:

[http://www.ubuntuforums.org/attachment.php?attachmentid=4646&d=1134924790](http://www.ubuntuforums.org/attachment.php?attachmentid=4646&d=1134924790)  :D :KS ;)

---

### Post by Zonkle on 2005-12-18
Thanks AI :D now I have MPlayer installed and everthing is working:D It was very very easy using Synaptic.

It installed alos XMMS :? but it's ok ...

There is an error msg when I open MPlayer and when I play anything says:
New_Face Failed.Maybe the font path is wrong.Please supply the text font file (~/mplyaer/subfont.tff)

What is that ?

Also in MPlayer menus ,,, it looks so old :? .. it doesn;t look like it is getting the Gnome theme .... why ?
Also when I do Full Screen for a movie, the screen goes full screen but the resulotion still the same :? so it is just black all around the video... didn't really go full screen.

Zolero thanks. But I don't think I need that. What is it any way?

BTW, I installed Gnome Bluetooth and it worked just great :D can I like synchronize contacts and stuff like that ??

It looks like I have to install the nvidia driver cuz i saw the 3D screen saver is slow .... can I also install from Synapatic :D?

Lotta love ;)

---

### Post by Perfect Storm on 2005-12-18
the font problem : 

```
sudo apt-get install mplayer-fonts
```

The mplayer looks old because it uses GTK 1 and aren't compiled with gtk2. In the next release it will looks more smoother and better.

Bluetooth I have no experience with. Perhaps you should make a seperate thread about it.

Which Nvidia card do you have...better what's your computer specs.

---

### Post by zolero on 2005-12-18
Hi Zonkle. :cool: 

Your sources.list is OK so how it shows here, and U'd applyed Automatix how I see... That's good too. About the sources update error U don't should to worry at all. But if this is botherin' U open sources.list in gedit and correct the problem manually, something like that:

make a backup of sources.list

$sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

now edit the list:

$sudo gedit /etc/apt/sources.list 

then remove or comment (hash in) the line(s) which sends errors upon updating, save the file and close gedit. Type:

$sudo apt-get update .... and now U don't receive the error message. Done.

Hali, zolero.;)

---

### Post by zolero on 2005-12-18
Hehe...

Is a very huge script which installs many apps on your compu. U must only select wich apps U want to install (Azureus, Java VM, Opera,Mozilla plugins, etc.). And it does grafically with zenity's help. Just try it!

Zolero.:cool:

---

### Post by Wolki on 2005-12-18
[QUOTE=Zonkle]
Also when I do Full Screen for a movie, the screen goes full screen but the resulotion still the same :? so it is just black all around the video... didn't really go full screen.[/quote]

This is usually a sign that you don't use the correct video output. Try xv in Preferences > Video, then restart playback. I'd probably install the nvidia drivers first, but you can try without them.


> 
It looks like I have to install the nvidia driver cuz i saw the 3D screen saver is slow .... can I also install from Synapatic :D?


Installing with synaptic becomes addictive :) Yes, you can. Some more detailed instructions are here (detailed, but should be really easy):
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by Zonkle on 2005-12-19
Thank you all for the great help and for making Linux a much better experiance for me :)

Artificial Intelligence, thanks for the help:) I will try it.

Wolki, I will try the settings you gave me. And yes, I think I'm getting addicted to it :D I meant the Synaptic.
In the Howto you told me about, it asks for linux-restricted-modules-386, what does it do?

Zolero, I think I don't need that script cuz I have the Synaptic and it has everything whenever I need anything, but thanks ;)

As for my computer spec:
[LIST]
[*]AMD Athon 64 3200+
[*]512 MB Ram
[*]120 GB Hard Disks
[*]nVidia Geforce 5200 Fx
[/LIST]

Man I swear, using my MSI Bluetooth on Ubuntu was much much more easier than using it on Windows XP! :D
Now I will look for some Bluetooth accessories ... softwares ..

Cya ;)

---

### Post by Wolki on 2005-12-19
[QUOTE=Zonkle]In the Howto you told me about, it asks for linux-restricted-modules-386, what does it do?[/QUOTE]

Kernel modules are drivers that are not compiled into the main kernel, for many reasons (to keep the kernel small, to make sure other people can distribute them separately, etc). Restricted modules are such modules that are not under a free license. They don't cost money (at least these ones don't), but they don't come with all the advantages of truly free software.

The 386 is for the type of kernel you've installed. linux-386 works on any (iirc pentium and up) machine, and there are some specific kernels that may lead to higher speed on these machines. Different modules are needed for each type of the kernel. Look here for more information: [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by Zonkle on 2005-12-19
Thanks Wolki.

I found like 3 "linux-restricted-modules-386" !! I have to install them all ?!

I have one of them installed.

---

### Post by Wolki on 2005-12-19
[QUOTE=Zonkle]I found like 3 "linux-restricted-modules-386" !! I have to install them all ?!

I have one of them installed.[/QUOTE]

No, you just need the one for the kernel version you have installed. Look at the output of "uname -r" and compare it to the version number. Usually, ubuntu installs the relevant restricted-modules automatically, so you can probably skip that step.

---

### Post by Zonkle on 2005-12-20
Thanks man that's great.

I'm downloading them right now :)

Thanks for the help.

---

### Post by bronwe on 2005-12-21
Hi Zonkle,

After using a different source.list repository and updating.  Use Synaptic to download mplayer-386, mplayer-plugin, and mplayer-fonts.  This will find the right libraries to get too.

Good Luck.

-bronwe

---

### Post by Zonkle on 2005-12-22
Thanks ;)

It is already working great :) thanks for every body.

I didn't download the mplayer-plugin though! ... what is it?

---

### Post by Perfect Storm on 2005-12-22
mplayer-plugin makes you see movies etc. in your web-browser.

---

