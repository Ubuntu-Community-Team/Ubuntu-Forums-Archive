---
title: "Ubuntu is not well"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ettienne on 2007-07-02
My Ubuntu is not running well, cannot connect to the internet, gives network & protocol errors, is dog slow and generally things are not going well.
I want to reinstall Ubuntu without loosing VirtualBox, is that possible?

---

### Post by Golyadkin on 2007-07-02
Try posting the results:
> 
free -m
df -h


Also, to keep your VirtualBox installation, just copy the virtual harddisk files somewhere safe, and you will be fine.

---

### Post by ettienne on 2007-07-02
free -m
> 
                   total       used       free     shared    buffers     cached
Mem:          1962        806       1156          0         86        547
-/+ buffers/cache:        172       1790
Swap:         5741          0       5741


---

### Post by ettienne on 2007-07-02
dh -h

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G   70G  143G  33% /
varrun                982M  112K  982M   1% /var/run
varlock               982M     0  982M   0% /var/lock
procbususb            982M   80K  982M   1% /proc/bus/usb
udev                  982M   80K  982M   1% /dev
devshm                982M     0  982M   0% /dev/shm
lrm                   982M   33M  949M   4% /lib/modules/2.6.20-16-generic/volatile


---

### Post by ettienne on 2007-07-02
I know I can copy the vdi files, but copying a 4GB file takes about an hour on my network from the Ubuntu computer to my Win2000 server. It takes less than 5 minutes to copy the same file from my WinXP to Win2000.
I have about 8 files to copy....
Something is real messed up on the Ubuntu side.

---

### Post by Golyadkin on 2007-07-02
Don't you have a DVD burner? You can burn those 4GB files much faster than copy them over the network. 

Your have more than enough free memory and free harddisk space, so I think the lag must be in something else. Have you tried disabling IPv6? I am not sure on how to do that, but it is explained on the forum here somewhere.

---

### Post by ettienne on 2007-07-02
Just as an aside, I have a 250GB external drive I thought I would hook up to the Ubuntu computer and copy my files. No go there either, Ubuntu says I do not own the drive - I have an invoice to prove that I do own it darnit!

---

### Post by ettienne on 2007-07-02
No DVD in my Ubuntu computer, it's in the other one :(

I disabled IPv6 in Firefox about:config, but no luck there either, still no internet access.

Everything was working 100% until I tried setting up shared folders (System, Administration, Shared Folders), I got a network error (cannot access [www.ubuntu.com/](www.ubuntu.com/)... something or other) and since then things have gone to hell rapidly.

---

### Post by Golyadkin on 2007-07-02
Try and restart your router if you have one. Also try and restart your networking layer: 
> 
sudo /etc/init.d/networking restart

and check for errors in the console.

---

### Post by ettienne on 2007-07-03
Problems solved - I installed Windows 2003 Server and all is running well.

Better the devil I know than the devil I don't.

---

### Post by kwacka on 2007-07-03
reminds me of that T-shirt - 'rehab is for quitters'.

Wouldn't you really - deep down - like to have got the problem beat.   ;)

---

### Post by ettienne on 2007-07-03
I would rather have something work, not crap out unexplained and then try and figure out why.

This is not my first attempt at Linux and will most likely not be my last. My first attempt was nearly 10 years ago on Red Hat, still in the early days. I have tried various distros and each one has crapped out at some point.
I believe there is a future in Linux, it's just not arrived yet...

---

