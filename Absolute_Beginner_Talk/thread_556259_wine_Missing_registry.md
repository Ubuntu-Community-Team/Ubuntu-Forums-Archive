---
title: "wine Missing registry"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-09-21
When I removed wine reinstalled it (for some reasons)](*,). I also did:

rm -rf ~/.wine

and after reinstallation of wine I also reinstalled the software but now when I run the application software, it gave this error and closed:
" Required registry information is missing and this application cannot run. PLease rerun setup to correct this problem."

Well, I did many times rerun it both wine installation and software installation but it does not get better. Any suggestions?
thanks 
findik

---

### Post by bubbalouie on 2007-09-21
Have you run **winecfg** ?

If I recall correctly that will build a registry for you. Last time I cleared out my wine folder (same method as you) I did this to rebuild it before installing my apps.

I hope this helps :)

---

### Post by findik1 on 2007-09-21
> **bubbalouie said:**
> Have you run **winecfg** ?

If I recall correctly that will build a registry for you. Last time I cleared out my wine folder (same method as you) I did this to rebuild it before installing my apps.

I hope this helps :)

yes, I opened that but what do I do with that? Wouls you please be more clear?

---

### Post by Bothered on 2007-09-21
When you run winecfg it will configure wine (I think it runs wineprefixcreate). Once you've run winecfg you can close the configuration program and wine should now work.

---

### Post by findik1 on 2007-09-21
> **Bothered said:**
> When you run winecfg it will configure wine (I think it runs wineprefixcreate). Once you've run winecfg you can close the configuration program and wine should now work.

wine seems working but the installed application program not. It gave:

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
regedit: Can't export. Registry key 'HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\ThemeManager' does not exist!
Success

regedit: Can't export. Registry key 'HKEY_CURRENT_USER\Software\Wine\AppDefaults' does not exist!
Success

regedit: Can't export. Registry key 'HKEY_CURRENT_USER\Software\Wine\DllOverrides' does not exist!
Success

---

### Post by bubbalouie on 2007-09-21
In my case I just setup the folder in desktop integration tab to point to more useful locations, and configured the sound device to work with ALSA and use 48khz 16bit. It seemed to do the trick. 

I also have done the following:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I find the 'bleeding edge' wine to be a little quicker and more stable than the version in the repositories.

In the case of your applications, is it ALL applications or just a single application that is misbehaving?

---

### Post by findik1 on 2007-09-21
> **findik1 said:**
> yes, I opened that but what do I do with that? Wouls you please be more clear?

application was working perfectly. I updated feisty and for some  resons rm wine and install , also did 
sudo rm -rf ~/.wine
and reinstalled the application and now application is not working due to registry error. I found in other linux forums comoon but  I am not that good in Linux, so could not understand the solution.

---

### Post by bubbalouie on 2007-09-21
I know this will sound like a cop out but, in this situation I would: 

Kill all of the processes associated with wine
Remove the ~/.wine
Install the 0.9.45 version of wine (it is much better) <- See here, then **sudo apt-get update && sudo apt-get upgrade**
Run **winecfg** and pick my settings
Install a simple known to work app to verify my system works
Install the app you need/want.

I appreciate it is a shotgun approach to the problem, though sometimes this guarantees a result as opposed to spending hours fooling around to get to the root of the issue.

Good Luck

Ryan :)

---

### Post by findik1 on 2007-09-21
> **bubbalouie said:**
> I know this will sound like a cop out but, in this situation I would: 

Kill all of the processes associated with wine
Remove the ~/.wine
Install the 0.9.45 version of wine (it is much better)
Run winecfg and pick my settings
Install a simple known to work app to verify my system works
Install the app you need/want.

I appreciate it is a shotgun aproach to the problem, though sometimes this guarentees a result as opposed to spending hours fooling around to get to the root of the issue.

Good Luck

Ryan :)

actually I am doing exactly what you are saying but it did not worked. So the only difference is I may install different version of Wine as you suggested, I hope it helps

---

### Post by findik1 on 2007-09-21
> **findik1 said:**
> actually I am doing exactly what you are saying but it did not worked. So the only difference is I may install different version of Wine as you suggested, I hope it helps

actually this new version of wine worked, thank you. However, Now I dont see any Wine related shorkuts in K menu like Wine file, .... Does anybody know how to add those?

---

### Post by bubbalouie on 2007-09-21
Right click an icon in the k-menu, select "edit item", then add a new item and treat it the same way you'd treat a new icon (link to application) on your desktop, you can even drop icons from the desktop into menus, remember to save changes when done :)

When launching the wine app a command of the following structure works well:

**wine "C:\Program FIles\ARMWSD\ARMWSD.exe"**

I recommend tarballing your ~/.wine when everything is peachy, I have noticed wine can slow down a touch if you try a few apps and then change your mind.

---

