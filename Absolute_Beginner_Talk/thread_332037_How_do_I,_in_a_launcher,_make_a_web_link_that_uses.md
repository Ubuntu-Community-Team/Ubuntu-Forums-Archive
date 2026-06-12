---
title: "How do I, in a launcher, make a web link that uses the non default browser?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Daveth on 2007-01-05
Hi.
I had hoped my first post here might be more "significant" but this simple problem has me beat. 

I have made a desktop launcher (dektop configuration file) with the url for this forum. If I leave it at that it works OK but opens into Firefox. I want it to launch into Opera instead. I have set preferred applications to Opera, but the link ignores that. Tried adding just Opera in front of the url but that does nothing.
I guess there is some code I'm missing that goes between the application and the url??

Can anyone help please?

Daveth

---

### Post by jimbo2150 on 2007-01-05
In the launcher's "command" line:

```
opera http://www.ubuntuforums.org/
```If you do a _*man opera*_ in the terminal you will see that opera's command line works like this:

    *opera [OPTIONS] [url]*

So by typing in the brower launch command followed by the URL, opera (instead of your default browser) will launch with the typed URL. Options are optional, if you need more info on options you can always do the *_man opera_* command in the terminal.

**EDIT:** Forgot this: If you are using GNOME (tan bars at top/bottom of screen) interface, you can set your default browser by using:
***    System -> Preferences -> Preferred Applications***
   A dialog will appear. Under Web Broswer (in the Internet tab) edit the browser or command line. If you want opera to be your default, choose it from the drop down menu. If it does not appear in the drop-down menu, choose 'Custom' and type in the command:
  ```
opera "%s"
```

---

### Post by Daveth on 2007-01-05
Hi Jimbo
Thanks for that. I thought the man pages were only for deep system stuff, so a useful pointer. Launcher works just fine now.
David

---

