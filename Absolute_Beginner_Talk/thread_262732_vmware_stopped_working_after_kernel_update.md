---
title: "vmware stopped working after kernel update"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-09-22
Hi, I updated my kernel to 2.6.15-27-386 and then VMware stopped working!

I search here and found no help, and then found out how to fix it, so here it is:-

The problem I has was that I could not get the VMWare configure script to recompile vmware for my new kernel as it/I could not find the kernel header files.

Well I didnt know they had to be manually downloaded!

So just type :
sudo apt-get install linux-headers-`uname -r` build-essential 

And then re-run the VMware configure script.

---

### Post by dmizer on 2006-09-22
yup ... mine did that too. i'm running fedora core, so i didn't have to recompile but the idea is the same.
```
sudo /usr/bin/vmware-config.pl
```

just for related reference, if something doesn't start, open a terminal and run the program that way.  it will give you extremely helpful error messages.  in the case of vmware, the error message says "vmware is not configured, you will need to run vmware-config.pl"

you have not lost any information.  once the vmware server is reconfigured, you will be able to load your previously configured virtual machine by the "open a virtual machine" option in the menu.

---

### Post by rbmorse on 2006-09-22
Don't forget to install kernel-headers matching the new kernel version before running vmware-config.pl

---

### Post by grizz_granlien on 2006-09-22
okay and you say istall kernal etc before reconfigureing well is there a step by step instuctions to resetup the get the Vmware working

---

### Post by iluminate on 2006-09-22
Greetings,
Think it was something like this -

```
sudo apt-get install linux-headers-`uname -r`
```
Long time I did it, but maybe some other can answer if correct.

Cheers

---

### Post by bulldog on 2006-09-22
Type 

uname -r

and write down the answer

sudo aptitude install linux-headers-answer

When done type

sudo /usr/bin/vmware-config.pl

and follow onscreen instructions,basicly a lot of enters :D

---

### Post by iluminate on 2006-10-03
> **bulldog said:**
> Type 

uname -r

and write down the answer

sudo aptitude install linux-headers-answer

When done type

sudo /usr/bin/vmware-config.pl

and follow onscreen instructions,basicly a lot of enters :D

Bulldog - What is wrong with ```
sudo apt-get install linux-headers-`uname -r`
```??
And then /usr/bin/vmware-config.pl

---

### Post by mcduck on 2006-10-03
> **iluminate said:**
> Greetings,
Think it was something like this -

```
sudo apt-get install linux-headers-`uname -r`
```
Long time I did it, but maybe some other can answer if correct.

Cheers

If you do it that way, you'll have the same problem again after next kernel update.

The right way is to install a metapackage called linux-386, linux-686 or whatever kernel type you are using. This package always depends on latest versions of _all_ kernel-related packages, so having it installed will make sure you always have correct versions of kernel, kernel headers, and restricted modules.

so if you are using 386 kernel, run 'sudo apt-get install linux-386', for 686 kernel 'sudo apt-get install linux-686', for k7 'sudo apt-get install linux-k7'.

Installing a specific version of kernel-related files will only get you troubles in future.

---

### Post by iluminate on 2006-10-03
Well then I know why I have always to reconfigure VmWare each time there is a kernel update =)
Thanks mister for the answer. I now know what to do and why.

---

