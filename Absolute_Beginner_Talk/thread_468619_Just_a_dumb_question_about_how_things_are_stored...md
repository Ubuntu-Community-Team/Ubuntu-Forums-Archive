---
title: "Just a dumb question about how things are stored..."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-06-09
When you install programs from packages in synaptic, they just install somewhere in the root directory, right? Whereas if you download a specific .deb or tar.gz, you extract them into your home folder. Correct? I just downloaded Azureus, and the folder is on my desktop. Can I throw it to the root directory somehow? If so, where's the ideal place to throw stuff like this that I downloaded?

---

### Post by riven0 on 2007-06-09
I think the programs you download from Synaptic goes through** /var/cache/apt**. The programs you downloaded yourself, though, you may be able to place it in the /var or /opt folder without messing anything up. Someone correct me if I'm wrong.

---

### Post by zvacet on 2007-06-09
All packages you download with synaptic or apt-get you can find in var/cache/apt/archives .But they are just stored there in case that you uninstall some file and maybe want to install it again.in that case you will not download file again because you allready have it in var/cache/apt/archives .
Most of installed packages goes to the usr/bin .If you have Azureus deb file on your Desktop just double click on it and will be installed and placed in correct directory by itself.You can allway chek it with 

```
cd /usr/bin
```

and see if Azureus is there.Maybe even better is to use these commands

```
whereis Azureus
```

or 

```
locate azureus
```

---

### Post by Roasted on 2007-06-10
when I do a locate azureus, it's all in my home folder. Can I just move it to another folder in root without it getting messed up? If so, what folder do you suggest?

Also, can I set up the launch file to be an icon under apps - internet? Because Azureus isn't listed there...

---

### Post by zvacet on 2007-06-10
It look like you didn´t install it.What type of file you downloaded,deb or tar.gz?I think that you can find Azureus in add/remove.Just in case try to type in terminal 
```
azureus
```

and see what will be

---

### Post by mikewhatever on 2007-06-10
> **Roasted said:**
> when I do a locate azureus, it's all in my home folder. Can I just move it to another folder in root without it getting messed up? If so, what folder do you suggest?

Also, can I set up the launch file to be an icon under apps - internet? Because Azureus isn't listed there...

No, you can/should not move it. The thing you've downloaded is not a folder, but an installation file. It should be called like this Azureus_2.5.0.4_linux.tar.bz2. That very version is in the repositories so you should just install it from synaptic.

---

### Post by FuturePast on 2007-06-10
The traditional place to unpack tarballs like azureus (that don't require compiling) is /opt.

---

### Post by Roasted on 2007-06-10
I redownloaded Azureus in the tar.gz folder and extracted it to /opt. At first it wouldn't let me, so I created a folder called Azureus there and gave it 777 rights. Even after I did that, I was still at the same problem I was before. Installation file? Well, if it's an installation file, why does it launch when I double click the Azureus icon? My torrents from last night still showed up... *shrug*

So I just did away with all of that and installed it from Synaptic. But even still, did I not install it the first time? Why did it still launch just fine? HOW would I of installed it? I saw no indiciation that told me it was not currently installed. 

Also, when I do a locate azureus, I still get a folder in my home folder that I guess is hidden. It's caleld /.azureus. I can't seem to get rid of it, even with rm -rf. How can I ditch this folder?

---

### Post by Nekiruhs on 2007-06-10
> **Roasted said:**
> Also, when I do a locate azureus, I still get a folder in my home folder that I guess is hidden. It's caleld /.azureus. I can't seem to get rid of it, even with rm -rf. How can I ditch this folder?
Don't remove it, thats all your Azureus settings. You home folder is where all your settings are kept.

---

### Post by Regel on 2007-06-10
When you have downloaded the azaureus-file (.tar.gz etc.) just extract it to your home folder.
Now you should find a folder 'Azureus'. There're multiple files in there, execute the file "azureus" or something like that. That should do the trick.
You can copy the folder to /opt/, and make a symbolic link from /usr/bin, so you would be able to run this version of azureus by just typing the command 'azureus'.

.deb files can be installed by typing sudo dpkg --install file.deb

---

### Post by Roasted on 2007-06-10
Regel, I just redownloaded and extracted it specifically in the /opt folder. 

However, I just deleted it and installed it from synaptic then.

---

