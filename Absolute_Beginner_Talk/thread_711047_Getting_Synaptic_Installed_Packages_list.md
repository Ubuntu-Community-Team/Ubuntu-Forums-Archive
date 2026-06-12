---
title: "Getting Synaptic Installed Packages list"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by karthikbalaji on 2008-02-29
I have a fully configured, "necessary-things-installed" ubuntu machine. Now i installed ubuntu in a new machine. I don't want to repeat the painful process of going through the entire synaptic list and select packages.

Is there any which through which I can dump the installed softwares list from my old machine and use it in my new machine ?

I didn't save the marking's while I was configuring my old machine :( .

Thanks

---

### Post by Teber on 2008-02-29
if you still, got the old machine you could look up installed with add/remove, selecting "installed". how to dump that list to printable file, which is what i think you may have in mind, is better answered by the real gurus...

---

### Post by karthikbalaji on 2008-02-29
If u look at synaptic  there is a option,

file -> Read Markings

I wish to generate a package list of the old machine that can be read by the new machine's synaptic

---

### Post by karthikbalaji on 2008-02-29
Ok this thread is the only thing I manged to find . Though it not a complete solution, it atleast saves 70 % overhead .

[http://ubuntuforums.org/showthread.php?t=576629](http://ubuntuforums.org/showthread.php?t=576629)

I guess its a better idea to write a full-fledged installation script keeping the things discussed in the above thread in mind...

---

### Post by julian67 on 2008-02-29
Here's a slightly simpler way using similar method, it should do exactly what you need.

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html")

---

### Post by jan quark on 2008-02-29
haven't used this option yet
but in synaptic under 

*file *

there is the option called

**generate package download script**

it generates a shell script so you can download the selected packages on another computer

---

### Post by karthikbalaji on 2008-02-29
Ya it generates script only for the selected packages. Not for the installed ones.

That is,

after selecting the packages to install if u use this option it ll generate a bash script. I guess this is used to do simultaneous installations at the same time.

---

### Post by kpkeerthi on 2008-02-29
> **karthikbalaji said:**
> 
Is there any which through which I can dump the installed softwares list from my old machine and use it in my new machine ?


It is quite easy to copy over the setup from Old machine to New machine if you know and understand what you do.

Assuming you have a separate / partition, OM - Old Machine, NM - New Machine

OM: 1. Tar up the / partition from your old machine. See [backup & restore ]("http://ubuntuforums.org/showthread.php?t=35087")with tar.
NM: 2. Perform minimal install
NM: 3. Boot using a Live CD 
[Yes. Step 4 through 9 are performed in Live mode]
NM: 4. Mount the / partition of new machine to /ubuntu
NM: 5. Restore the tar image you created in step1 to / . See [backup & restore ]("http://ubuntuforums.org/showthread.php?t=35087")with tar.
NM: 6. Modify /ubuntu/etc/fstab to suit the disk partition scheme of the new machine *
NM: 7. Optionally, Edit /ubuntu/etc/modules and remove the modules you do not need * 
NM: 8. Edit /ubuntu/boot/grub/menu.lst and correct the path to vmlinuz according to partition scheme of the new machine *
NM: 9. Exit Live CD and reboot normally. 

* You may also backup fstab & menu.lst from your new machine prior to restoring the tar in step 5 and the copy them over again.

---

### Post by drs305 on 2008-02-29
On the old machine, run this to create a file  <filename> in your home directory with the installed packages listed:
```
sudo dpkg --get-selections >~/filename
```

Copy this file to the new computer to your new computer's home directory, then run the following to read the list and install the packages:
```

sudo dpkg --clear-selections
dpkg --set-selections <~/filename
sudo aptitude install dselect-upgrade

```

---

### Post by jldeshpande on 2008-02-29
> **karthikbalaji said:**
> I have a fully configured, "necessary-things-installed" ubuntu machine. Now i installed ubuntu in a new machine. I don't want to repeat the painful process of going through the entire synaptic list and select packages.

Is there any which through which I can dump the installed softwares list from my old machine and use it in my new machine ?

I didn't save the marking's while I was configuring my old machine :( .

Thanks


Yesterday I read about  'partimage'.
Search for   'Partimage.html'   &  'Partimage-manual_Usage.html'
With this ,we can take backup of our present installation [complete '/'partition] on a dvd.It becomes a bootable dvd as 'Partimage' gets installed on it.This dvd  is a backup of your Ubuntu OS for recovering in case of any misshapen & i think from this dvd you can also install your present  Ubuntu OS on new machine along with all softwares you have installed.
Such things i have done in  'Windows' & will try in Ubuntu shortly.Before playing /experimenting with your OS,a backup is a must.Twice in this week my Ubuntu was unbootable & with help of this forum members i recovered.Now  without doing anything risky,i am going to take backup.
 You should have a live Ubuntu cd for this ,because mounted partitions can't be taken by 'Partimage'.So boot from live cd,download  'Partimage' by enabling  'universal' repository.It will get installed in RAM, Do the things as per usage.html mentioned above.
Best luck!
Pl. post feedbacks  which will be useful for others.

---

