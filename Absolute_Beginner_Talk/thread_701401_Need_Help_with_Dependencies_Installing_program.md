---
title: "Need Help with Dependencies Installing program"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Hipenbecker on 2008-02-19
I have Ubuntu Installed and it appears to be running.

I want to install "Handbrake".  I found a .deb for the Ubuntu GUI and I downloaded it.

It tells me something along the lines on "Dependency Mono" is not satisfied.

I have found documentation of what I need to do. and refers to a command line like 
sudo apt-get install mono

I open up a terminal window.  I type in the command, hit enter and it 

which gives me an error (package not found)

Can anyone help with the procedure for getting the packages so I can get these commands to work and hopefully resolve dependencies.

Thanks

---

### Post by Dr Small on 2008-02-19
It may be in the universe repository. Have you enabled all repositories?

---

### Post by yabbies on 2008-02-19
need to make sure all your repositories are open

I'm assuming you are using Gutsy 7.10

System>Admin>Software Sources

check to make sure all repos are open(checked)
main, universe, multiverse, restricted.

then try again
also sometimes it easier to open synaptic

System>Admin>Synaptic Manager

and do a mono search for the dependency you want.

---

### Post by Hipenbecker on 2008-02-19
Thanks everyone.  I will try that and let you know if that is it.

---

