---
title: "Update repository without internet"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Battalion on 2008-03-10
Hi, I'm using Kubuntu 7.04 and i have no internet connection for my pc at home.  I would like to update my repository from the pc at work.  At work there is a linux ftp site with everything: main, restricted, universe and multiverse repositories.  

What I would like to know is if its possible run a script on my home pc with all the packages necessary for update and put in on a 8gb usb then take it to work and run the script to download the packages to my usb.  When i get home then i can just apt-get to a directory with all the downloaded packages.  Is it possible?

---

### Post by handydan918 on 2008-03-10
Probably not in quite the way you describe.
The trouble is that the home machine has no way to know what packages are available.
I can't work out all the details for you, but something along the following lines might work.

1) On home machine, run ```
sudo dpkg --get-selections>>whatever_you_want_to_name_this_textfile
```

2) Same thing on work machine, but different file name

3) Compare the two files (maybe use diff?) and download the changes to your usb drive from the work machine to be installed on the home machine.

Sorry, that's all I can think of.

That said, updating a Linux box is not likely to be as critical in terms of security as it is with windows. First of all, windows updates only once a month. Second, there just aren't as many exploits out there to runagainst Linux. So if you updates are lagging, but it all works. you're still better off with a Linux box than a fully patched windows machine.

---

### Post by YoG%*@ on 2008-03-10
hi, 

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) might be what you are looking for.

hth,
mux

---

### Post by gandaran on 2008-03-10
there is a way to do  what you want, but using a cd,  it's aptoncd.
look for APTonCD in add/remove programs or synaptic.

---

### Post by Battalion on 2008-03-10
Ok thanks i'll try the APTonCD package.  But will it require me to install Kubuntu on my work pc also or can i run it as livecd and create an image (.iso) with k3b so i can write it later after ejecting the livecd?

---

### Post by Battalion on 2008-03-12
Ok I used aptonCD on my work pc and downloaded necessary packages then created a repository aptoncd .iso file.  On the pc without internet at home, i restored the image using aptoncd and it copied all the packages to /var/cache/apt/archives.

Now what i want to know is how to install these packages automatically rather than individually and having to setisfy dependencies?!

---

### Post by Battalion on 2008-03-31
I have used aptoncd to update my pc without internet but it seems that randomly some packages become damaged while making the restore iso image.  This seems to be a problem with the application but it still works nicely and only damages about 2 packages per iso.  

To avoid the damaged packages, i found that the installed packages are actually stored in /var/cache/apt/archives so i can retrieve them manually and put them on a usb drive.

Thanks for all your suggestions

---

### Post by Irihapeti on 2008-03-31
You might find this useful for installing packages automatically, including dependencies:

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

---

### Post by Battalion on 2008-03-31
> **Irihapeti said:**
> You might find this useful for installing packages automatically, including dependencies:

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

Do you mean packages in a folder on the harddrive or from the internet?

---

### Post by Hutom on 2008-03-31
Check the link in my signature.

---

### Post by Irihapeti on 2008-03-31
I haven't used nonetdebs myself, but I understand it's a way of downloading all the packages you need for a particular program so that you can then install them on a non-networked computer.

Another method, which I have used, is to use the option "generate a package download script" (under synaptic file menu) which you can then run on another computer. Then, when you've transferred the downloaded files to the non-networked machine, select "add downloaded packages". You are then asked to select the directory where you've put the downloaded packages, and the programs are loaded.

The only problem with this second method on a non-networked machine, is that your repository listings don't get updated. It may be possible to manually copy the files from a networked machine, but it's not something I've tried.

---

