---
title: "disk cleanup: what is necessary?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by lastredoubt on 2007-03-10
Hello,

I've read a beginner's book on the ubuntu distro, introducing linux in the process, and I have a question not answered by the book about system maintenance.  Coming from Windows, it seems like every time I used the internet, or installed a program I needed to cleanup the drive and registry with various utilities such as ccleaner and winreg.  Is this a necessary task in Linux and if so, how does one go about it?

Thanks,
Daniel

---

### Post by buuntuu! on 2007-03-10
forget about all of these things :)
linux-filesystems work in quite a different way than ntfs/fat
having the disc defragmented does not determine your systems speed here. (don't ask for details for i don't know them either ;)

install all your programs from the command line with
```
sudo aptitude
``` and you'll be fine (no dependencytroubles)
see [psychocats]("http://www.psychocats.net/ubuntu/aptitude") page for details
welcome to linux!

---

### Post by mikewhatever on 2007-03-10
Sort of. There is no registry equivalent in Ubuntu. The residual packages (installation leftovers can be cleaned from synaptic or terminal). Cookies and temporary files are cleaned using Firefox, which actually does the job.
For more look here [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by fasoulas on 2007-03-10
About defragment tools...the equivalent in linux is every 30 times u log on ubuntu you will see something like memory check and it takes 2-3 minutes to finish  i had the same question a while ago  Don't worry you don't need such things like ccleaner or winreg  Have fun using ubuntu :)

---

### Post by lastredoubt on 2007-03-11
Thanks for all the help and links to further resources -- much appreciated!

---

### Post by xyz on 2007-03-11
Just in case you'd want to change this, run:
```
sudo tune2fs -c 50 /dev/hdx
```
It's "50" you'd want to change; for instance 10 ...will mean it'll chkdisk at the 10th reboot.
If you want to force a chkdisk at next boot:
```
sudo -s
```
```
cd /
```
```
touch /forcefsck
```

---

