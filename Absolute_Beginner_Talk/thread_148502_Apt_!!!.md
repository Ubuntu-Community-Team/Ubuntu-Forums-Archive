---
title: "Apt !!!"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by faisalnet5 on 2006-03-22
Hi everyone... 

I have one very funny question though i am totally a new Linux user (i think) but really i need help.

I know a bit about apt's functionalities....but from the Terminal with a sudo root authority when i typed apt.....it said      apt: command not found

Can anyone help me plz....i want to install one software.

---

### Post by dermotti on 2006-03-22
Use **synaptic** if yer a newb

---

### Post by localzuk on 2006-03-22
If you want to use apt-get from the command line, you have to use it via sudo. So to run an update type:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

This will only work in an admin enabled account (such as the one you created when you first installed Ubuntu). It will ask you for a password - this being the same as your user password.

HTH

---

### Post by frodon on 2006-03-22
I second the dermotti's advice, synaptic is a frontend to apt commands and it's really easy to use : [https://wiki.ubuntu.com/SynapticHowto?](https://wiki.ubuntu.com/SynapticHowto?)
Checks also this link, it specify the repositories you may want to use : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by tomski on 2006-03-22
you can type:

synaptic   = gui frontend for apt-get
aptitude   = text based front end for apt-get
apt-get install packagename   = install a package
apt-get remove packagename   = remove package
apt-cache search packagename  = query apt for info about a package

there are alot of other switches(command options) for apt-get, so continue to use synaptic whilst reading up on apt-get. 
you can also type man apt-get to veiw the 'manual' pages for apt (and for any other just use 'man command')

this may help too:

 [http://www.apt-get.org/](http://www.apt-get.org/)  (use 'find' function of browser to search page for ubuntu) 
should give you lots of info plus a list of all repositories(remote locations where packages are stored) but only use the repositiories for your OS (in your case ubuntu breezy) otherwise you will create all sorts of problems

hope this helps

---

### Post by tribaal on 2006-03-22
Something we should maybe make clear is that although "apt" is what we refer to while discussing, the actual command is *apt-get* :)

It took me quite a while to get this figured out, people just tell you to "apt something" when you actually should type:
```
sudo apt-get install *something*
```

Otherwise, use synaptic, which is both convenient and easy to use...

Hope this helps :)

---

