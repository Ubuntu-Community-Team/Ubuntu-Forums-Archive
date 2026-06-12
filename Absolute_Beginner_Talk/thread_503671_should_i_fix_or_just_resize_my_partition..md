---
title: "should i fix or just resize my partition."
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by jtesolin on 2007-07-18
When I installed Ubuntu, i successfully resized my windows partitions to allow me room for Ubuntu in the free space (used the guided partition). I now realize that while 7-8GB fix everything I would like to make my partition at least 40.

However, I created an extended partition for the guided install to use. Would this be a problem? Should I fix the partitions before I resize? I have included a .png of my partitions.

---

### Post by mikewhatever on 2007-07-19
It does not matter if the partition is extended or primary, no need to fix it. In fact, you can't turn it into a primary.
How are you planning to resize? There seems to be nowhere to expand.

---

### Post by jombeewoof on 2007-07-19
that doesn't look like it would be easy to resize without being a real pain.
an easier route would be to boot back into windows, and create another ntfs drive in your extended partition. and mount that under C:\Program Files\*newfolder* you would just have to make sure you intstalled any new apps to C:\Program Files\*newfolder*\new app

sure that's still a pain, but you wouldn't lose any data, and wouldn't have to reinstall either

---

### Post by jtesolin on 2007-07-19
Mike and Jom, thanks for the replies. Hmm...I guess I won't be able to resize. I will try the suggestion of installing apps to the C:/ drive. How would I do that? I know I installed an app that will automatically mount my drive in Ubuntu. Do I just edit source list?

---

### Post by bodhi.zazen on 2007-07-19
**You can easily resize that partition with gparted !!! **

The "trick" is you need a newer version of gparted and you will need to do this with your hard drive un mounted.

Try the gparted live CD : 

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by mikewhatever on 2007-07-19
> **jombeewoof said:**
> that doesn't look like it would be easy to resize without being a real pain.
an easier route would be to boot back into windows, and create another ntfs drive in your extended partition. and mount that under C:\Program Files\*newfolder* you would just have to make sure you intstalled any new apps to C:\Program Files\*newfolder*\new app

sure that's still a pain, but you wouldn't lose any data, and wouldn't have to reinstall either

I must second the question. How do you install Linux applications to C:\Program Files...? I don't think you should be posting such misleading information.

Jtesolin, you have no other option but to redo the partitions and reinstall. If you have some removable media at hand, you can try backing up the whole of the root partition before deleting it.
[http://psychocats.net/ubuntu/backup](http://psychocats.net/ubuntu/backup)
[http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage)

Note, the root partition has 5 GB of data. Try running the following commands to get rid of temporary and residual packages
> sudo aptitude clean
sudo apt-get autoremove

---

### Post by bodhi.zazen on 2007-07-19
> **mikewhatever said:**
> Jtesolin, you have no other option but to redo the partitions and reinstall.

That is not true. Newer versions of gparted, as found on the gparted live CD, will resize Jtesolin's partitions with no problem (he has sufficient free space).

Please, if you do not know, do not advise, it only confuses the issue.

---

### Post by mikewhatever on 2007-07-19
Are you saying he can shrink sda2 and then drag sda5 to the left to enlarge? That would be nice.

---

### Post by bodhi.zazen on 2007-07-19
> **mikewhatever said:**
> Are you saying he can shrink sda2 and then drag sda5 to the left to enlarge? That would be nice.

Yes. The older versions of gparted (the ones on the ubuntu desktop CD's) can not do this, but newer versions can :twisted:

And yes, it is very nice indeed.

He could also move swap and resize sda3, adding to sda5

---

