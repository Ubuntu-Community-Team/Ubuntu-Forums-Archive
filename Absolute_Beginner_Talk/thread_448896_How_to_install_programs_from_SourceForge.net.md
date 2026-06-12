---
title: "How to install programs from SourceForge.net"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-19
Hi, does anyone know how I can install programs from SourceForge.net?  More specifically I want to download the [FreeMind]("http://sourceforge.net/projects/freemind/") program.  I downloaded the files they had but I couldn't figure out how to install it.

---

### Post by bobplano on 2007-05-19
get the .deb then 
```
 sudo dpkg -i /path/to/freemind 
```

---

### Post by Bachstelze on 2007-05-19
They have a DEB package in their releases. Download that and install it with

```
sudo dpkg -i filename.deb
```

---

### Post by adam_kimber on 2007-05-19
Usually it is wiser to get files from the Repositories as compilation is not required. 

Most programs downloaded from Sourceforge will be in source format, or src. This means that they are just code and there are not binaries, i.e. the program to run. To get a binary (program) from source code compiling is required.  This thread has more on that. [http://ubuntuforums.org/showthread.php?t=425891](http://ubuntuforums.org/showthread.php?t=425891)

AS for the Freemind program, if you download the freemind-bin-0_8_0.zip file that is an already compiled binary that can be run. 

Do the following, download the file, right click on the zip file in Nautllus and click extract here. 
Rick click on freemind.sh (the binary) and go to the properties, then permissions tab. Then check "allow executing file as program", click OK. Now double click the freemind.sh file and clcik run. Presto :D

---

### Post by zhinker on 2007-05-19
Thanks guys.  I actually managed to find a different way to download it before I saw your posts.  There were some instructions on this site:
[http://sourceforge.net/project/shownotes.php?release_id=355162](http://sourceforge.net/project/shownotes.php?release_id=355162)
on how to add the repository for that and download it directly from there.  It's probably better that way because now I'll be getting the updates for it if it gets any (right?)

But it's still good to know the other ways for anything else I might want to download, so thanks again!

---

### Post by zhinker on 2007-05-19
> **adam_kimber said:**
> Usually it is wiser to get files from the Repositories as compilation is not required. 

Most programs downloaded from Sourceforge will be in source format, or src. This means that they are just code and there are not binaries, i.e. the program to run. To get a binary (program) from source code compiling is required.  This thread has more on that. [http://ubuntuforums.org/showthread.php?t=425891](http://ubuntuforums.org/showthread.php?t=425891)

AS for the Freemind program, if you download the freemind-bin-0_8_0.zip file that is an already compiled binary that can be run. 

Do the following, download the file, right click on the zip file in Nautllus and click extract here. 
Rick click on freemind.sh (the binary) and go to the properties, then permissions tab. Then check "allow executing file as program", click OK. Now double click the freemind.sh file and clcik run. Presto :D
Hey Adam, it turned out the program I downloaded from the repos was the beta version and they didnt' have the last stable version available there (at least not as far as I could see) so I ended up installing it from the zip file like you said and it's working beautifully now, thanks :D

Just one question, I'm not sure where exactly the programs are meant to be saved in Ubuntu (I've 'found' multiple folders that seem to have programs saved in them.  Could you please point out which one I should save the freemind files in (for the sake of organization?).  Plus, how do I get the program to show up in my Applications menu?

---

### Post by Bachstelze on 2007-05-19
Usually, such programs are installed in /opt.

---

### Post by zhinker on 2007-05-19
> **HymnToLife said:**
> Usually, such programs are installed in /opt.
Thanks, I assume opt stands for optional files?

---

### Post by loathsome on 2007-05-19
Programs are usually placed under /usr/, either bin, sbin or local.

---

### Post by Bachstelze on 2007-05-19
Not programs installed with a binary tarballs... Yes, basically, /opt stands for optional files, meaning that you should be able to delete everything in it at any time without it affecting your system at all. It's mostly used for programs you install yourself, as opposed to programs you used an installer for. Those should usually put in /usr/local but most Linux systems nowadays just put them in /usr.

---

### Post by Merlin 3 on 2007-05-28
> **adam_kimber said:**
> Usually it is wiser to get files from the Repositories as compilation is not required. 

Most programs downloaded from Sourceforge will be in source format, or src. This means that they are just code and there are not binaries, i.e. the program to run. To get a binary (program) from source code compiling is required.  This thread has more on that. [http://ubuntuforums.org/showthread.php?t=425891](http://ubuntuforums.org/showthread.php?t=425891)

AS for the Freemind program, if you download the freemind-bin-0_8_0.zip file that is an already compiled binary that can be run. 

Do the following, download the file, right click on the zip file in Nautllus and click extract here. 
Rick click on freemind.sh (the binary) and go to the properties, then permissions tab. Then check "allow executing file as program", click OK. Now double click the freemind.sh file and clcik run. Presto :D

Help....!   Did exactly as you said here and nothing happens at all ...no response full stop!
Any idea what might be wrong?

---

### Post by cymen on 2007-05-28
Let's try from the command line then!

Open up a terminal, and use "cd" to navigate to wherever you extracted the file. For example, if you downloaded the file to the Desktop and then extracted everything there you'd do:

```
cd Desktop
```

Then you'll want to run the freemind.sh:

```
./freemind.sh
```

---

### Post by weigh2tall on 2007-05-29
Not to jump in the party too late but if you're comfortable with editing your /etc/apt/source.list, there is a very easy way to install free mind.

Run
```

  sudo nano /etc/apt/sources.list

```
  This will bring up your apt-get sources with in the terminal
  You can replace nano with gedit if you want a gui way to do it.

Add these two lines 
```

  deb http://eric.lavar.de/comp/linux/debian/ experimental/
  deb-src http://eric.lavar.de/comp/linux/debian/ experimental/

```
  Save (Ctrl-X) then 'y' then 'enter'

Then run
```

  sudo apt-get update
  sudo apt-get install freemind

```

Answer yes to the prompts and you should have a working freemind right away.
It should be in the Applications Menu under Office

---

