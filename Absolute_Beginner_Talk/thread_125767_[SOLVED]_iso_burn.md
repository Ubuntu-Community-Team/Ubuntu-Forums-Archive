---
title: "[SOLVED] iso burn"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by madmetal on 2006-02-04
just finished dapper iso download and i don't find nautilus to write it!
where should i look? would nautilus write it as an .iso?

---

### Post by sprok8 on 2006-02-04
Are you running Ubuntu now? Nautilus is the default file manager, and can be found at Applications | Accessories | File Browser

As to whether it will write an ISO, I actually don't know since I use K3B for burning CD's and DVD's. It's really a nice program, very easy to use and full featured.

---

### Post by Madpilot on 2006-02-04
Nautilus writes ISOs very well.

Start Nautilus with **Places Menu --> Home Folder**, find your ISO, and right-click on it. Select "Write To Disc", make sure there's a blank CD-R in your burner, and let it run.

---

### Post by madmetal on 2006-02-05
thanx madpilot it works great!
i am writing the iso at low speed in order not to have problems during the installation.
k3b is the kde burning utility  i am using gnome is there any problem installing k3b?

---

### Post by 8086 on 2006-02-20
there is no problem in using kde applications with gnome. use synaptic or
```
sudo apt-get install k3b
```

---

### Post by soonindallas on 2006-02-20
or you can use gnomebaker to write iso images:

applications > sound & video > gnomebaker

choose "burn cd image" option

---

### Post by noteforself on 2006-02-20
hi all,

i'm using the latest dapper drake daily build on an amd system with gnome.  i just installed k3b.  when i run it, i get this message, "cdrdao will be run without root privileges"

can someone kindly help me configure my system so that i can run cdrdao with root privileges?  thank you in advance.

-hai

---

### Post by dvarsam on 2006-02-21
My guess is this:

In the Windows Wold, to run MS Word, basically you run "Winword.exe"

You should try to do this:

Find the appropriate "executable" in the Linux World that RUNS your program & then perform a "chmod" to restrict the permission for the program to run for a single USER.

Case Solved:
Your program will NOT be able to RUN from any user - but ONLY from ROOT.

Hope I helped.

---

### Post by 8086 on 2007-05-24
> **dvarsam said:**
> 
Find the appropriate "executable" in the Linux World that RUNS your program & then perform a "chmod" to restrict the permission for the program to run for a single USER.

Case Solved:
Your program will NOT be able to RUN from any user - but ONLY from ROOT.

Hope I helped.
Are you high on acid, dvarsam? That is just plain wrong. And not the answer he was looking for either. Actually, I have no idea what you tried to answer. In order to run cdrdao with root-privileges you prefix the command with sudo, such as this:
```
sudo cdrdao name-of-tocfile.toc
```

Since you can use sudo as the default user, there is no use for the other way, which leaves you theoretically open to security flaws, but here goes:
Find the executable and add the SETUID bit (set user id). That will make the executable run as the user that owns it (in this case, root). So this would be ```
sudo chmod +s /usr/bin/cdrdao
```
Now you will run the program as root every time.

---

