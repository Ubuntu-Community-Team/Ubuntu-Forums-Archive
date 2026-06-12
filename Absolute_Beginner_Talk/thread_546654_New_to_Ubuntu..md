---
title: "New to Ubuntu."
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Who_am_I on 2007-09-09
Hi everyone! Today just installed the Ubunto OS into my old com. ):P 

I'm using Ver, 7.04(is it the latest version?) :confused: Have a few questions to ask, hope theyr nt stupid questions. :mrgreen: 

1) when uninstalling programme, will it be like Windos whihc will leave some threats behind? 
2) where to get new programmes? :confused:
3) Am i able to get my online games to work in Ubuntu? 

Currently, just these 3 questions first. When i think of more questions, will post them. :p

Thanks all Guru(s) in advance.

---

### Post by tripokey on 2007-09-09
> 1) when uninstalling programme, will it be like Windos whihc will leave some threats behind?
The settings will be left behind in your home folder so when you reinstall you will get the same settings.
> 2) where to get new programmes?
Applications->Add/remove
> 3) Am i able to get my online games to work in Ubuntu?
if you are reffering to windows games check [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Who_am_I on 2007-09-09
Hi tripokey.

Do u mean if totally wan del the programme, mus also del the file leave behind in home folder? :confused:

Thanks for ur fast reply. :)

---

### Post by hashimoto on 2007-09-09
The program itself will be totally removed, the only thing that will be left are your personal preferences and settings for the program (so no "running code" left behind). 

The settings & preferences will be in a hidden file in your home folder and you can see them by selecting Places > Home Folder and then from the menu View > Show hidden files.

---

### Post by por100pre1 on 2007-09-09
When we talk about your home folder we mean the folder:

```
/home/*your-user-name*
```

actually a folder with your user name inside a folder called home.

That's where your files and settings are saved.

---

### Post by lioninthesky on 2007-09-09
> **por100pre1 said:**
> When we talk about your home folder we mean the folder:

```
/home/your-user-name/
```

actually a folder with your user name inside a folder called home.

That's where your files and settings are saved.

Just to expand on that, your settings will likely be in a a 'dot' folder within your home directory.  

For example, if you install and run GFCEU (Gnome FCE Ultra - rom emulator), your settings for the program will be installed in:

```
/home/your-user-name/.gfceu/
```

There are some exceptions to this.  An example would be  Rhythmbox (Gnome Media Player).  The settings for this program will be installed in:

```
/home/your-user-name/.gnome2/rythymbox/
```

I'm not sure off the top of my head what constitutes the reasoning why some Gnome programs have settings in your root home directory and some layered into .gnome2 under your root home directory.   Perhaps someone else can clear that up.  Anyway, Gnome aside, it is a good idea generally to look at the first example as a place for your settings, whether you want to remove them or change them.

---

### Post by Who_am_I on 2007-09-09
Hi all.

thanks for fast replies. =D> I learn new things today. 

I downloaded wine, but i cant seen to make it run......:confused: any help? 

Thanks.

---

### Post by tripokey on 2007-09-09
When installing wine you should follow this guide [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

And here is an introduction on how to use it. [http://linux.strangegamer.com/index.php?title=Using_Wine](http://linux.strangegamer.com/index.php?title=Using_Wine)

Unfortunately this can be a bit daunting to new linux users but its not impossible and you will probably learn a lot about linux on the way.

---

### Post by koshari on 2007-09-09
while wine can be a good application to get something you need to run its very hit and miss, 

unfortunately Linux's strong point generally isn't windows gaming, 

on the other hand any online java games should play fine with a linux disto and the java runtime files.

---

### Post by lioninthesky on 2007-09-09
> **lioninthesky said:**
> Just to expand on that, your settings will likely be in a a 'dot' folder within your home directory.  

For example, if you install and run GFCEU (Gnome FCE Ultra - rom emulator), your settings for the program will be installed in:

```
/home/your-user-name/.gfceu/
```

There are some exceptions to this.  An example would be  Rhythmbox (Gnome Media Player).  The settings for this program will be installed in:

```
/home/your-user-name/.gnome2/rythymbox/
```

I'm not sure off the top of my head what constitutes the reasoning why some Gnome programs have settings in your root home directory and some layered into .gnome2 under your root home directory.   Perhaps someone else can clear that up.  Anyway, Gnome aside, it is a good idea generally to look at the first example as a place for your settings, whether you want to remove them or change them.

I should have mentioned, you don't *have* to use these directories.  In most cases you'll be able to modify the settings from within the application itself.  Also, regarding security/performance, you don't have to delete the settings folder after removing the package/application.  That's really just a matter of preference.

Either way, handy information to be aware of.

---

