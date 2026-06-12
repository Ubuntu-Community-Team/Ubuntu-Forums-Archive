---
title: "whoops, made a package installing faux pas, and am not sure what to do."
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Javaguy on 2007-04-02
Hi, Its the end of my first day with Ubuntu, and I think I have already broken something... I wanted to install OpenTTD ([http://www.openttd.org/index.php](http://www.openttd.org/index.php)) so I could play it when not in windows. I downloaded the package and went to install, but then a message came up in the console saying I needed to copy the files. I attempted to click "ok" but couldnt, I tried to press enter, spacebar etc- still nothing. I then closed the package install thing, which was probably a bad idea... 

anyway. I have re-downloaded the ottd package, but now when I try to install it I get an error saying "only one software management tool is allowed to run at the same time", even when I have JUST logged in and opened nothing else. Whoops.... have I just broken my Ubuntu? 

after the error comes up and I click close "installing package file" comes up on the bottom of the package manager window, but nothing else happens. I assume this is a bad sign.... 

re-installing Ubuntu is, fortunately still a viable option, but I would be concerned if I managed to break it with such ease.... :(

anyway, thanks in advance- I am learning about linux gradually :)

oh, while Im here, how do I find out the dot clock speed of my graphics card to set a custom resolution? Is it just the core processor clock speed? 

thanks!

---

### Post by rjfioravanti on 2007-04-02
have you done a full restart?

usually try and keep separate questions in separate posts

---

### Post by Javaguy on 2007-04-02
mm, I have turned off the computer completely for a reasonable length of time.

oh, the second question was a just an aside, I may post it in the revlevent topic soon :)

---

### Post by bapoumba on 2007-04-02
Only one package manager can run at a time. There is a lock file in /var/lib/dpkg that handle this. If you are sure that no other ackage manager is running, and thus giving you the error, delete the lock file (another one will be created when needed). Open a terminal (> Accessories > Terminal) and run:
```
sudo rm /var/lib/dpkg/lock
```
Do you have errors running:
```
sudo aptitude update 
```

---

