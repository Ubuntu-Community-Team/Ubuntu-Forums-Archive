---
title: "4 issues: music files, partition, LaTex &amp; upgrade"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by sweettea on 2006-08-12
I've installed Breezy on my laptop, using the default settings, which allows for dual-operating systems and created a partion. The Dapper cd has been ordered and I am awaiting its arrival. In the meanwhile I would very much like to resolve the issues disscussed below. Much obliged to any assistance in any of these.

I am having difficulties with the following in no particular order:

(1) Music files
I would like to be able to access my old music files from the Windows partion. 

(2) Partion
I would like to remove the Windows partion as well as everything to do with Windows after I sort the music files.

(3) LaTeX
I have been running LaTeX via MikTex in Windows. I would like to set up LaTeX and Kile in ubuntu. I have a TexLive 2003 cd which comes the a recently purchased LaTeX companion book, and will receive TexLive new release from TUG. (While waiting, I would like to use LaTeX.)

I attempted to install TexLive following the suggestions at [http://ubuntuforums.org/showthread.php?p=807144](http://ubuntuforums.org/showthread.php?p=807144) and between step 4 and step 5 received the following message:

   ...
   done copying
   system updated successfully
   since you already had files in /usr/TeX/texmf/web2c
   We have not touched anything there. 
   Please review your setup

Which I am interpreting to mean the system has located the TeX (Windows) files and isn't inclined to install over them.

the PATH directory path, does not exist (ie, /usr/local/texlive/2005/bin/i386-linux) and it appears that because of the presence of a previous TeX installation, TeXlive is not going to install.

I have attempted, to set the PATH in the /etc/bash.bashrc a to the following:

   PATH=/usr/local/TeX/texmf:$PATH; export PATH

Naively hoping I could just 'point' to the current version of TeX, to no avail. (I have since removed the PATH line from the bash.bashrc file.)

Secondary to this, I thought to install Kile using the Add Applications and  recieved the following message:

   "Cannot install 'kile'. Installing this application would mean that
    something else needs to be removed. Please use the "Advanced" mode to
    install 'kile'."

No idea what to do now.

(4) Not as pressing as the above but interesting is that I am unable to upgrade to Dapper via the Breezy update manager which indicates that 

   your system is up-to-date

Which obviously it isn't, when the `reload' button is pressed the following message occurs:
    
   There is a new release of ubuntu available

Followed by a pop-up message indicating packages have been downloaded.

I've read the update notes which indicates I should be able to highlight and install the update. There is nothing to highlight and I can not figure out how to get the updated packages to install. 

I am perfectly content to await the arrival of a cd as problems (1) to (3) are more pressing. Thanks.

---

### Post by TFX360 on 2006-08-12
Well, I get access to my windows partitions via System / Administration / Disk. Then they suddenly appear in my /tmp. Dunno why but I have to do this every time. Maybe I need to add them in my fstab but I'm being a little cautious. Then I can read the windows disk but not write. This is a little harder. I believe it is possible with ntfs-3g or g3. One and two should be solved for you then. Three I know absolutely nothing about. Good luck with that one!


Kind regards,

TFX

---

### Post by RRS on 2006-08-12
> (1) Music files
I would like to be able to access my old music files from the Windows partion.


Follow [this guide]("http://easylinux.info/wiki/Ubuntu#Windows") to mount your windows partition so you can access your files. You won't be able to write to the partition but you can copy from it and paste the files to another partition, including the one containing Ubuntu.

> (2) Partion
I would like to remove the Windows partion as well as everything to do with Windows after I sort the music files.

Glad to hear that, but you might want to wait till you've finished upgrading to Dapper and have everything set up and functioning to your satisfaction. Just as a sort of "fallback" in case you want to experiment.

As for your music files and deleting windows, do you have enough room to move the files completly out of the windows partition? In order to entirely delete windows I believe you'll have to reformat (erase) the entire partion so your music, and anything else you want to save, will have to be backed up elsewhere first.

> (3) LaTeX
Sorry, can't help with this one. Actually I don't even know what it is.

I had upgraded to Dapper when it was still pre-beta by changing my sources lists but  I didn't think that was needed after the official release. You might be able to find an old thread in the Breezy section of the forums so you don't have to wait.

Otherwise can you download and burn to a cd? If so the alternate(text based) is slighty better to use then the desktop (live). [Here's]("http://users.bigpond.net.au/hermanzone/index.htm") a good tutorial.

I think this should at least put you on the right path, post back if you have problems or more questions.

---

### Post by sweettea on 2006-08-13
Thank-y'all for the help with music files. 

By following the instructions at the link provided I've been able to view the windows partition and copy the music files over to the Ubuntu partition.

And I've taken the advice on board about not eliminating Windows until I've installed Dapper. Good advice! I'll be patient for the time being, but Windows' days are numbered.

One problem solved! Much obliged.

---

### Post by sweettea on 2006-08-13
Situation update:

I deleted the old TeX directory and subdirectory then reinstalled TeXlive from the cd. Still unable to set the PATH, however I was able to use Add Applications to install Kile. I successfully compiled a LaTeX file. Just need to configure Kile to view the dvi or pdf file. 

Thanks SO much for the help! Will consult when ready to wipe Windows off!

---

### Post by junglepeanut on 2006-08-13
So the only thing left is wait for CD?

Did you change your source.list yet?

i.e.

If you have breezy right now it says something like

deb: http blah blah breezy universe blah blah

but you want it to read

deb: http blah blah dapper universe blah blah

so everywhere you have breezy change to dapper, some of the editors have a find and replace so it will be real fast will little chance for error.

---

### Post by junglepeanut on 2006-08-13
Oh yeah, kile has loads of settings options its easy to get lost in them. I have installed a few styles etc packages and what not. Sometimes it gives me the I can't find so and so, when I run the check install wizard. But I must have my path correct as when I compile they work. 

Good luck

---

### Post by sweettea on 2006-08-13
No, I've not changed the source.list, afraid I could really mess things up, and ignorance of where to find the file, but I might give it a go this evening.

So far, so good with Kile, but I've not tried to install packages yet. I'm attached to MikTex's method of auto-install so this might be new hurdle to get over. 

Thanks so much for the tips, keep them coming!

---

### Post by junglepeanut on 2006-08-20
/etc/apt/sources.list


location of source lists. Also search the wiki for source.list in the text and there is one that is something like source-o-matic, this is great for the new to linux as far as adding to your repositories, although as you get used to your source.list you will change it yourself.

Also I don't recall if texmaker came with texlive, but if kile feels full of options etc. Or you hate the time it takes for it to initialize because you are under gnome etc. Texmaker is nice for quick changes. But kile is somewhat lovely as I use it for all programming.

---

