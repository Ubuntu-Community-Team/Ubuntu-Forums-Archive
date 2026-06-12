---
title: "Updated / Upgraded Am I sure?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by YeahBuntu on 2006-09-16
I recently installed ubuntu... I am so impressed.  I am attempting to setup my own webserver.

Was wondering. I used sudo apt-get install apache2 ...

Does gnome automatically detect I did installed something outside of gnome and will update/upgrade as necessary when there are updates?

Another question .. is there a way I can setup the gnome desktop to display things like ... memory usage /hard drive space / cpu usage / number of users connected and what thier login names are?

Thanks in advance

---

### Post by baldy1324 on 2006-09-16
i dont really get your 1st question, but for your second check out a tool called gkrellm, which shows all your cpu, memory... ```
sudo apt-get install gkrellm
``` you can then run it by typing ALT-F2 to bring up run and type gkrellm

---

### Post by aleska on 2006-09-16
I think the 1st question is in regards to using command line apt-get versus synaptic package manager.  According to the Desktop help on Adding, Removing and Updating Applications, both Synaptic package manager and Add/Remove Programs are actually based on APT.  So, I'm pretty sure that intalling apache2 through apt-get will provide you with the same updates through update manager that you would get had you installed through synaptic.  You should be good to go.  However, I think it is important that whatever app you are installing is from a repository in your sources.list file.  So sometimes if you install something that isn't part of the ubuntu repositories, you will have to add a repository reference in that file to get updates. (I think) 

Also, it may not be exactly what you are looking for, but if you right-click in one of your panels and select Add to Panel, there is program called system monitor which monitors cpu stuff.  Once its up and running you can right click it to select preferences to edit what is being monitored (processor, monitor, network traffic, swap usage, etc.)

Hope that helps.

---

### Post by emprog on 2006-09-16
For question 2, you can also install gdesklets
sudo aptitude update
sudo aptitude install gdesklets

---

### Post by YeahBuntu on 2006-09-16
When I typed in those commands the last one gave me this response:

Couldn't find any package whose name or description matched "gdesklets"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by emprog on 2006-09-16
you might have to enable multi/universe repositories for that.

---

### Post by YeahBuntu on 2006-09-16
Wow those little applet things are EXACTLY what i was looking for.... one question tho .. they are realllly small on my desktop and I cannot seem to (strech them and make them bigger..) is there no way to do that... I can barely read what some of them are reporting.

---

