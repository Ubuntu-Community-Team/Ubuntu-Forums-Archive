---
title: "Palm Book/Newsreader Equal?"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Djanvk on 2005-08-04
I'm looking for programs that would be equal to the windows version, the programs I'm looking for are:

In Windows was using iSiloX to convert eBooks to iSilo format and read them in iSilo on my Palm PDA.  are there any other readers for the linux system that does this or comparable.

Next
I use Plucker on my Palm to read rss feeds off sites, was using Sunrise in windows to capture the RSS feeds and get them ready to send to my plucker in my Palm PDA.  Are there any program which to this in Linux?

Trying to convert fully to Ubuntu, sick of crashing windows and have mostly converted what I did in windows to ubuntu, but not all yet.


Thanks for any help.

---

### Post by xbaez on 2005-12-07
Plucker Desktop works allright
I got it working, except for the images, I get a
[img error: Bad image type]

Apart from that it works ok, I install the pdb files after I download them to my hard drive.

I've googled a lot and I haven't found anything usefull

---

### Post by martinbriscoe on 2005-12-31
>>>>
Plucker Desktop works allright
I got it working, except for the images
<<<<

I think plucker is as good as isilo on the palm. Only problem for me is that I havent been able to get plucker desktop working on my pc. so I have to go back to windows to add new plucker documents.

I have downloaded the plucker desktop using the package manager. It seems to have installed it in that I can see a plucker desktop folder in usr/share but I cant see  how to launch it.

Any ideas would be appreciated.

Martin

---

### Post by nomediakings on 2006-01-07
I run Sunrise on Ubuntu, although I haven't found a package for it. I downloaded it from [here]("http://sourceforge.net/project/showfiles.php?group_id=151061") and ran sunrise-desktop.sh ... I have it put the feeds in a folder and then drag them to the gnome-pilot applet -- after it syncs I read them with Plucker. It's a bit clunky but it works. I find Sunrise easier to use than Plucker Desktop, which I spent forever trying to get to sync to my Palm.

And I don't read books on the Palm that often but I'm pretty sure OpenOffice allows you to save docs to .pdbs, which then you could drag to the gnome-applet to sync.

---

### Post by martinbriscoe on 2006-01-09
Thanks to help from the plucker desktop forum. I Now have plucker working perfectly with ubuntu including images.

Sadly I am not quite sure what fixed the problem. 

But first I had to be able to run the desktop by creating a launcher (rt click >'create launcher) then in the command box enter /usr/bin/plucker-desktop

I then had to track down pluckerrc (its in /etc) and edit this using gedit so that the comment 'image_parser = netpbm2' no longer had the ;;s in front of it. 

Ideally the package <plucker_1.8-9ubuntu1_i386.deb> should be tweaked so that it automatically adds it to the program menu and sets the package up to work 'out of the box' 

Martin

---

### Post by palmdoc on 2006-01-14
[QUOTE=nomediakings]I run Sunrise on Ubuntu, although I haven't found a package for it. I downloaded it from [here]("http://sourceforge.net/project/showfiles.php?group_id=151061") and ran sunrise-desktop.sh ... I have it put the feeds in a folder and then drag them to the gnome-pilot applet -- after it syncs I read them with Plucker. It's a bit clunky but it works. I find Sunrise easier to use than Plucker Desktop, which I spent forever trying to get to sync to my Palm.
[/QUOTE]

Hi. Total Linux noob here. Am trying to migrate to Linux and would love to get Sunrise running on Ubuntu. I have downloaded Sunrise Linux and extracted it to a folder on my dekstop. 
Does one just run the shell script like this:
sudo sunrise-desktop.sh
in a terminal?
If I do I get 
sunrise-desktop.sh: command not found 
which is strange because I have navigated to the correct folder

Thanks
:confused:

---

### Post by palmdoc on 2006-01-20
*bump*
I used Automatix to install the latest Java - do I have to install the Java SDK too?
Please help thanks.

---

### Post by palmdoc on 2006-01-21
Hmm. Feel like I'm talking to a wall here :P
Anyway FWIW, it seems to be working now - with the command
sudo sh sunrise-desktop.sh

Now to figure out command line schedule options.....

---

### Post by Daniel McLaws on 2006-01-21
I have been able to load hotsync plucker documents to my palm T/E through Kpilot (on Knoppix) but still trying to get plucker desktop to properly install on Ubuntu. I can download the rpm, but then at a loss as to how to install it on my desktop.

DJM

---

### Post by palmdoc on 2006-01-21
[QUOTE=Daniel McLaws]I have been able to load hotsync plucker documents to my palm T/E through Kpilot (on Knoppix) but still trying to get plucker desktop to properly install on Ubuntu. I can download the rpm, but then at a loss as to how to install it on my desktop.

DJM[/QUOTE]

Daniel, don;t bother with the rpm - just fireup the Synaptic Package Manager and search for Plucker - you'll see the Plucker Desktop option for installation...
I prefer Sunrise over Plucker since the Plucker Desktop supports only web pages but Sunrise gets the RSS feeds too.

---

### Post by lulucamargo on 2006-06-20
PalmDoc,
I followed your footsteps to run Sunrise here, but I did not succeed, I get the message:
Unable to access jarfile sunrise-desktop.jar

Do I have to edit sunrise-desktop.sh anyhow? Like, provide a path for java or something?

---

### Post by MantenaBr on 2006-10-04
hi Lulucamargo,

I got the same error message here. This is how I solved it:
Just edit sunrise-desktop.sh and add
> cd /path/to/sunrise-0.42j/
in the beginning

Hope it helps ;)

---

### Post by wastrel on 2006-10-09
I've been using Pyrite Publisher for years to convert text and stuff to palmdoc format.  

It's in the universe repository, the package name is pyrite-publisher.

It is a command line program, use 

```
pyrpub somefile.txt
```

to create somefile.pdb, a palmdoc version which you can read in your favorite doc reader.  

pyrpub supports html input and several output formats.

---

