---
title: "Text Editors and sudo, issues with . . ."
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by thale on 2006-09-05
I gave this a search but the word sudo is entirely too popular so I apologize if this is redundant.

The issue I'm running into is when I launch JEdit or gedit from the applications bar I am unable to save any files I have edited. I get a premission denied.

However, when I launch gedit with sudo from a prompt everything is a-ok (of course).

So what I'm asking is how can I run a text editor from the application bar and still have it run in sudo or at least be able to save files.

---

### Post by aysiu on 2006-09-05
```
gksudo jedit
``` or ```
gksudo gedit
``` should help you.

---

### Post by davmac on 2006-09-05
If you own the file and have the relevant permissions you can use gedit without prefixing with sudo.

If you want to see the ownership and permissions for a file, open up a terminal go to the relevant directory and type "ls -l". If you want to change the ownership of a file have a look at the chown command, and to change permissions the chmod command.

If you do need to run gedit with sudo from the application bar try prefixing it with "gksudo".

Hope this helps,

Dave Mac

---

### Post by aysiu on 2006-09-05
Generally speaking, if you don't already have permissions on a file, it's a very bad idea to *chown* or *chmod* it unless you know what you're doing.

---

### Post by thale on 2006-09-05
I am some what new with Linux in general so please excuse my ignorance.

So if I prefex the launch command inside link in the applications bar with gksudo that should do the trick? or do I need to just run this once in the command line and ubuntu will take care of the rest?

---

### Post by thale on 2006-09-05
> **aysiu said:**
> Generally speaking, if you don't already have permissions on a file, it's a very bad idea to *chown* or *chmod* it unless you know what you're doing.

Yeah I'd really like to avoid that. I'm programming in Ruby on Rails and it automaticly generates a lot of files when it set's up the framework so that's why I'm running into this issue.

---

### Post by aysiu on 2006-09-05
```
gksudo nautilus
``` is probably a good way to get around this, as it will launch an instance of Nautilus with root privileges (that temporary escalation of privileges is limited only to that Nautilus window and disappears once you close the window).

---

### Post by mssever on 2006-09-05
> **thale said:**
> Yeah I'd really like to avoid that. I'm programming in Ruby on Rails and it automaticly generates a lot of files when it set's up the framework so that's why I'm running into this issue.

Unless you've got an exotic setup, there's no reason that Rails can't run with your normal permissions. And it should, because root privileges should only be used for system tasks/files--which Rails isn't. If you're starting a project, just type rails as a normal user (without sudo). For exising projects, do ```
sudo chown -R youruser /path/to/rails/folder
``` In the very unlikely event that this breaks something, then your system is misconfigured somehow.

If you can't write to your web server's DocumentRoot directory as your normal user, you can either chown it, as well (sudo chown youruser /path/to/DocumentRoot) or ```
sudo chgrp yourgroup /path/to/DocumentRoot && sudo chmod g+rwx /path/to/DocumentRoot
``` Your group can be any group you are a member of. At the minimum, you're a member of a group with the same name as your username.

EDIT: Webrick doesn't need root privileges, either, unless you want to run it on a port <= 1024. It defaults to port 3000, IIRC.

---

### Post by stuoolong on 2006-09-05
> **aysiu said:**
> ```
gksudo nautilus
``` is probably a good way to get around this, as it will launch an instance of Nautilus with root privileges (that temporary escalation of privileges is limited only to that Nautilus window and disappears once you close the window).

This can also be done in Gnome by selecting from the Applications menu>System Tools>Run as different user, then tapping in nautilus as the program to run. :)

---

### Post by thale on 2006-09-05
> **mssever said:**
> If you're starting a project, just type rails as a normal user (without sudo). For exising projects, do ```
sudo chown -R youruser /path/to/rails/folder
``` In the very unlikely event that this breaks something, then your system is misconfigured somehow.

If I am not mistaken I get an error when I run rails with out sudo. I could be wrong however. Also, I'm using xubuntu (not that it matters too much). But I will give it a shot as well.

---

### Post by mssever on 2006-09-05
> **thale said:**
> If I am not mistaken I get an error when I run rails with out sudo. I could be wrong however. Also, I'm using xubuntu (not that it matters too much). But I will give it a shot as well.

If so, could you give me the error you get? I run rails without sudo without difficulty. It could be that you don't have write permissions in the directory where you're running rails (see my previous post for instructions on how to fix this).

---

### Post by thale on 2006-09-06
> **mssever said:**
> If so, could you give me the error you get? I run rails without sudo without difficulty. It could be that you don't have write permissions in the directory where you're running rails (see my previous post for instructions on how to fix this).

I got it all figured out. Haha, I was told you needed to use sudo to do pretty much EVERYTHING so whe I created a working dir in my home dir I used sudo to create it and thats where everything went down hill. I did a chown on the working dir and that cleared it all right up. 

The Error I mentioned I was getting was premissions related. On a side note, I did get cisco vpn and rdp to work which where the last to things keeping me from going full ubuntu on my other boxes ;)

---

### Post by mssever on 2006-09-07
> **thale said:**
> I was told you needed to use sudo to do pretty much EVERYTHING
I guess you've probably realized by now that that isn't true. You only need sudo for  certain system tasks. Here's my advice: Until you get a feel for what requires sudo and what doesn't, try everything *without* sudo first. Then, if you get a permissions error, use sudo. You can't damage anything by doing that, and the more experienced one becomes with Linux, the more one tries to avoid using root privileges unless absolutely necessary--it's just safer to avoid sudo whenever possible.

---

