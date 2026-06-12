---
title: "I need major help."
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by drosera88 on 2006-07-30
I just installed ubuntu. When it loads it comes up with a screen similar to DOS mode. I'm not sure what to type in. I just want to run the OS. It asks me to log in, which I do, then it waits for more commands. It says something about "sudo" and the "root" account. It says I need to set an administrator password. What should I do? Any help appreciated. Sorry if the answer is really simple.

---

### Post by Jagot on 2006-07-30
Try typing 'startx' when you're logged in.

---

### Post by confused57 on 2006-07-30
Did you happen to do an OEM install with the alternate CD?

Just a guess on my part...sorry, but I'm not familiar with the error otherwise.

Thanks Jagot, that was my other guess...good advice.

---

### Post by drosera88 on 2006-07-30
Actually, Im not sure, I may have. I installed ubuntu server, I didn't realize it untill I tried the previous suggestion. Could this be the issue? To be more specific, once I log in, I get a prompt that looks like this:

mynamemyusername:~$

I have no idea what to input. I tried startx, but that didnt work.

---

### Post by Jagot on 2006-07-30
If you installed Ubuntu as a server then there is no graphical user interface.  However, you can download it.  From Terminal:

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by drosera88 on 2006-07-30
I tried those and it didn't work. It said that it "couldn't find package named ubuntu-desktop"

Since I installed the server version, is there a prompt to uninstall ubuntu  server so I could install the desktop version?

---

### Post by confused57 on 2006-07-30
First, you might try enabling your repositories... after you've logged in, enter:

```
sudo nano /etc/apt/sources.list
```
press "enter" 
enter your password, press "enter"

Then uncomment(remove the #) in front of anything that looks like a url. Save the file(the ^ is a symbol for the Ctrl key).

Then at a console prompt, you can try the commands given by Jagot.

If this doesn't work, you can just install the desktop version over top of the server install.

See this guide;
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

Edit:  Jagot, I didn't think enabling the extra repositories was necessary, but since they would need to reinstall anyway...it would be worth a shot and a learning experience, also.

---

### Post by Jagot on 2006-07-30
> **drosera88 said:**
> Since I installed the server version, is there a prompt to uninstall ubuntu  server so I could install the desktop version?

Nope, you'd have to download either the alternate or desktop (live) cd.  The package ubuntu-desktop does exist and you should not need to enable any other repo's to get it to work:

[http://packages.ubuntu.com/dapper/base/ubuntu-desktop](http://packages.ubuntu.com/dapper/base/ubuntu-desktop)

Is the computer you're using this on connected to the internet?

---

### Post by drosera88 on 2006-07-30
Yes its connected, but I dont think Ubuntu detected the connection. If I just download the desktop version and run the CD, will it overwrite or update the server version??

---

### Post by Jagot on 2006-07-30
> **drosera88 said:**
> Yes its connected, but I dont think Ubuntu detected the connection. If I just download the desktop version and run the CD, will it overwrite or update the server version??

You can install it over the server installation.

---

### Post by drosera88 on 2006-07-30
Sweet, thanks, I appreciate it. I couldn't have done it without everyones help. I'm too linux illiterate...he he he...:KS

---

### Post by confused57 on 2006-07-30
I'm not sure I was any help, but it's best to run the Desktop LiveCD on your computer before trying to install...to check for possible hardware compatibility problems, especially graphics, wireless, modems, etc.  If the LiveCD runs OK, then installing shouldn't be a problem.

What are your system specs(CPU, ram,  video graphics card, type of internet connection, etc)?

---

