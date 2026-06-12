---
title: "[SOLVED] edit sources.list through a bash script"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2008-03-12
Hi, 
I want to write a bashscript to automate installations and such when I do a fresh install. I need to edit sources.list in order to activate the repos (partner repos and medibuntu and such, or whatever the kids are using nowadays). I don't know which command i need to replace text.
Can anybody point me in the right direction?

Mods feel free to move this to the right subforum if needed.

---

### Post by handydan918 on 2008-03-12
man sed

---

### Post by drs305 on 2008-03-12
You can use the echo command to add lines to sources.list
```
sudo su -c 'echo newline >> /etc/apt/sources.list'
```

You can use sed to change lines:
```
sudo sed -i 's/oldtext/newtext/g' /etc/apt/sources.list
```


You can read about them by viewing the man pages or searching for sed and echo.

---

### Post by hyper_ch on 2008-03-12
or you can create your dream sources.list and back it up the gpg keys and just copy those back (when needed)...

---

### Post by quinnten83 on 2008-03-12
> **drs305 said:**
> You can use the echo command to add lines to sources.list
```
sudo su -c 'echo newline >> /etc/apt/sources.list'
```

You can use sed to change lines:
```
sudo sed -i s/oldtext/newtext/g /etc/apt/sources.list
```


You can read about them by viewing the man pages or searching for sed and echo.

Is there an easy way to just uncomment that which is allready there?
beacuse I don' t know the GPG key of the ubuntu repos, that I thought, perhaps just uncommenting the repos in the sources.list would be easier.
I allready thought about using echo to add lines to the list.

I will look up SED in the man.

---

### Post by quinnten83 on 2008-03-12
Man, 
that man page is really cryptic. I would not have know what to do if you guys hadn't given an example.
one question though, if i need to replace a string, how would I go about that.
I am looking it up on google, but this might be more time effective.

---

### Post by quinnten83 on 2008-03-12
Okay, 
I figured it out, tried it and it worked
I just needed to use \ to escape the spaces
and the sed command needs to be eclosed in quotes.

---

