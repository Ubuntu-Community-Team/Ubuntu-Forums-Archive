---
title: "Building a poor man's ESX - Use Ubuntu Desktop or Server for the base OS"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by ekmack7 on 2007-10-05
Hello, 
We are doing a physical to virtual migration to ESX servers in our windows based network.  i also have some nice dell servers that I do not have the licenses to run as ESX servers.  I  don't want to get rid of them, and plan to run vmservers on them for  development. 

I would like to rebuild those physical servers from the current windows os to a linux os, to make patch management easier, as well as devote more resources to the running VM images.

My dilemma is do I install Ubuntu desktop for ease of use running the vmservers(and take the hit on resources), or find a way to manage the VMservers on the ubuntu server.  I myself am comfortable with command line, but I am cycling off this project, and my replacements are experienced windows admins not linux, and will be more comfortable with a gui.

Any recommendations on the easiest way to make this work, would be appreciated.

---

### Post by CrucifiedEgo on 2007-10-05
Sounds like you've got your answer then -- use xubuntu to save some ram, but go with a desktop install.  Windows admins are generally afraid of the command line, and those really good ones that are okay with it are generally confused by things like # and $.

-J

---

### Post by bsharp on 2007-10-05
or you could go with a server install and do 
```
sudo apt-get install fluxbox xdm
```
That will install xdm which is a Graphical Login Manager like GDM along with fluxbox which is even lighter than Xfce.

*Note for other people replying: I know about Fluxubuntu already having Fluxbox installed by default, but at the time of writing it isn't available for download until Gutsy is out.

---

### Post by ekmack7 on 2007-10-05
Do either of those two options have a advantage during remote administration?  I like sticking with the xubuntu desktop idea, I think the new admins will find it friendlier.  
thanks!

---

