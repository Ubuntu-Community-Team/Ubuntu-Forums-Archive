---
title: "Permissions not Granted!!"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by singlewc on 2007-11-10
I sat in front of my Ubuntu system pretty much all day. Wanted to install vmware server, again.... 

Got Vmware server installed, put the icon on the menu bar. Click it, and it opens beautifully, so I set up a windows 2000 guest. Installs fine. Runs fine. Setup service paks, and installed VMware tools. Great. All is well.

Need to access other filesystems/partitions to get the work done, so I stop the vm, and edit the settings to add a disk.

"sorry, you have no permissions to do this." 

Heavy sigh.... Got to a terminal, run sudo vmware, and add disks/partitions as needed.

Close terminal, click on Vmware icon at task bar. Nothing.....

Open terminal, run vmware..... Sorry, you don't have permission....

Run sudo vmware. Vmware opens, and tells me I don't have permission to access this file (what file that is, I have no idea......

Okay, now I am really upset, so I su to root, and run vmware. Sorry, no permissions to open the virtual disk!!!  I thought root could do ANYTHING on the machine. How can root be locked out of accessing the virtual disk???

After a full day of work, I can no longer access my virtual machine.

Count me as really agitated, but open to suggestions. This thing worked like a charm, until I had to add partitions, and it refused me permission. Why on earth is Ubuntu pissing so much with permissions? I made the virtual machine and VMware open, no private.

This is the second time I have gone down this road, and come to the same stupid ending. Last time, I deleted vmware completely, and tried virtual box, which is okay, but I like vmware server. So far, two days of my life wasted.... Sorry, but I am bummed as I fail to see why this OS freaks out so easily over permissions.

I go to terminal and check the vmware files, and they are all set to john john for permissions. That is the only use on the machine, other than root.

I don't want to just get back into vmware. I want to learn wtf is going on. The goal is to ditch windows, and us the VM for the handful of apps I need  until I get used to linux. 

I am listening if anyone can help. 

Thank you for your patience and willingness to help. Sorry to be upset, but this permissions thing, having to sudo to myself over and over and over, is very taxing, and when it blows up an entire day's work, its not easy to have a smile on my face.....

John

---

### Post by LaRoza on 2007-11-10
> **singlewc said:**
> 
Okay, now I am really upset, so I su to root, and run vmware. Sorry, no permissions to open the virtual disk!!!  I thought root could do ANYTHING on the machine. How can root be locked out of accessing the virtual disk???

Sorry, but I am bummed as I fail to see why this OS freaks out so easily over permissions.



Could you describe the problem more, this sounds familiar and I will look for the solution.

The reason why Linux (and all *nix systems) are concerned with permissions is security. Unix and its relatives are built around networking. Windows lets any user access any disk or partitions, unless the format is NTFS and it is explicitly set to be private. This is very unsecure. Windows makes things easy, I know, it also makes it easy to destroy you system with a double clicking a a text file, just because that file has a .bat extension.

The permissions and security of Linux are one area in which it excels, although it does require a more in depth knowledge of the system.

---

### Post by Zeosa on 2007-11-10
First try and determine what it's denying you permission to...if it's not telling you in the error output you'll have to get creative....


Try 'strace vmware' ....

A bunch of stuff that'll likely make no sense to you will scroll through the terminal until it gets to the error that halts the program (permission denied) ....look through the last page or so of output from that and see if you can determine exactly what it's attempting to open that it cannot (it'll be there somewhere)...

---

### Post by singlewc on 2007-11-10
> **LaRoza said:**
> Could you describe the problem more, this sounds familiar and I will look for the solution.

The reason why Linux (and all *nix systems) are concerned with permissions is security. Unix and its relatives are built around networking. Windows lets any user access any disk or partitions, unless the format is NTFS and it is explicitly set to be private. This is very unsecure. Windows makes things easy, I know, it also makes it easy to destroy you system with a double clicking a a text file, just because that file has a .bat extension.

The permissions and security of Linux are one area in which it excels, although it does require a more in depth knowledge of the system.


Well, I think I explained what I did. I installed it. Ran it, and when I edited the machine, I no longer had permissions.

Truth be told, I never destroyed a windows installation by clicking the wrong icon. That is an urban legend.

I really would like to know the answer to the other question. Since when does root not have permissions to do anything on the  machine? Since when did root, become subservient to some other group or user? How come when I run vmware as root, it cannot open the virtual disk (or some other file as it says) because it doesn't have the proper permissions? 

Ubuntu may have great permissions, but in my case, it has blown up my install, twice. I won't get all nasty :-) but so far, if this is great, you can have it.  I don't need fort knox, I need to be able to install, and run programs. 

I also appreciate you help, and hope you can see that I am just really frustrated at wasting two full days of my life, and still not having a working VM.

Thanks,

John

---

### Post by singlewc on 2007-11-10
> **Zeosa said:**
> First try and determine what it's denying you permission to...if it's not telling you in the error output you'll have to get creative....


Try 'strace vmware' ....

A bunch of stuff that'll likely make no sense to you will scroll through the terminal until it gets to the error that halts the program (permission denied) ....look through the last page or so of output from that and see if you can determine exactly what it's attempting to open that it cannot (it'll be there somewhere)...

I could post the output from where it starts to get ugly, but its rather large. The command works, and there is information that probably means something to someone :-) 

The error is about half a dozen little boxes, that simply say I  have 'no permissions' to access the file, and finally when I turn on the installed virtual machine, it claims it cannot open the disk, or 'some other file' because I don't have permission.

I am still wanting to know when things changed to where root cannot open and run any file on the system.

Thanks a lot. 

John

---

