---
title: "Confused with screen placement"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by godInAnAlcove on 2007-11-22
I am completely new  to Linux, so this is going to make quite a few of you grit your teeth I'm sure.  But here goes.

I have successfully completed the install using the alternate image, and I have been loaded to what appears to be a desktop.  But what I think should be the top left corner is about 1/3 of the way down the screen, and 1/5 of the way from the right.  And I haven't been able to find a way to adust this.  

All that is visible to me is an "Options" button and since things go off the screen, all I can see when it is clicked is "Restart", "Shut down", "Suspend", and "Hibernate".

So my question is, how do I correct this and make my iBook usable?  I can't see anything visible on the desktop to click and I don't know any kepboard shortcuts to open what I can't see :(

Thanks a bunch for any help!  I am really excited to learn more about Ubuntu and participate in the community!

---

### Post by godInAnAlcove on 2007-11-23
bump

---

### Post by mali2297 on 2007-11-23
I don't know what is causing the problem, but I can help you with some troubleshooting..

When you get to the login screen (the one you have trouble seeing), hit Ctrl-Alt-F1 to get to a text console.

Login via the console and then type
```

sudo /etc/init.d/gdm stop
startx

```
You should then get to a desktop.

If you still can't see more than part of the desktop, hit Ctrl-Alt-Backspace to get back to the text console. Then type
```

sudo dpkg-reconfigure xserver-xorg

``` 
You will be asked a bunch of questions, try to answer them as best you can. If uncertain, just press Enter and the default will be chosen. When done, try again with
```

startx

```

---

