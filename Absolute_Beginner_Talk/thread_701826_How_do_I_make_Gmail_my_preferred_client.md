---
title: "How do I make Gmail my preferred client ?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by ecr959 on 2008-02-19
Hello, everybody.  

          When I am bouncing around from one website to another, if I click on an email link,  I DON'T want Evolution to start, I want the Gmail compose screen, to start.  I know it has to do with the Desktop ,   I goto System - Preferences - Preferred Applications, I see the Email Reader and it says Evolution.  The only other choice is Custom.  Now ,  can some of you fine forum members tell me what do I have to type in that Custom "command" box ?     I will use Evolution only if I really have to, but I would much prefer to use Gmail.

Thank you in advance.:)

---

### Post by ph1 on 2008-02-19
By default, any link clicked online will open in a local email program, rather than a service like Gmail, which is accessed on a remote server.  This is an issue in Windows, too--I got rather tired of Outlook coming up every time I clicked a link.  

If you're using Firefox, try using [greasemonkey,]("https://addons.mozilla.org/en-US/firefox/addon/748") a little extension that can run user-defined scripts.  You can then pick scripts that fit the bill from userscripts.org; search for Gmail or Google and you'll find some neat results.

Alternatively, there seem to be some pre-packaged addons for Firefox, such as [Better Gmail]("https://addons.mozilla.org/en-US/firefox/addon/6076").  

Of course, for most of these you need to be logged into gmail continuously, or you need to log in every time you click a mailto link.

---

### Post by timbounceback on 2008-02-19
```
firefox www.gmail.com
``` might do the trick

---

### Post by Golem XIV on 2008-02-19
I found this procedure in [this post on the Serbian Ubuntu Users forum]("http://www.ubuntu-rs.org/forum/viewthread.php?tid=3013"), which was in turn taken from [this article in KomBib]("http://www.kombib.co.yu/vest.php?o=51&s=2532").  It may be just what you need.  Translation follows:

Just go to System \ Preferences \ Preferred Applications

Under Mail Reader, choose Custom, and then type the following into the Command box, changing "geek" to your username.

/home/geek/open_mailto.sh %s

Next we need to create the shell script (called **open_mailto.sh**) to your user folder ( /home/username ).

Create the script as follows in gedit:
```
#!/bin/sh
firefox https://mail.google.com/mail?view=cm&tf=0&to=`echo $1 | sed 's/mailto://'`
```
and save in your home folder as **open_mailto.sh**

If you wish the script to open a new tab in the existing Firefox window, use the following line instead:
```
firefox -remote "openurl(https://mail.google.com/mail?view=cm&tf=0&to=`echo $1 | sed 's/mailto://'`,new-tab)"
```
You may also want the script to be hidden from view.  In that case rename it with a period (.) in front: **.open_mailto.sh**. Of course, you will have to change the file path in the above parameters.

Finally, open a terminal session and type in the following command to make the script executable:
```
chmod u+x ~/open_mailto.sh
```

Keep in mind that the script will not log you on to Gmail automatically. 

Hopefully this will help.

---

### Post by seventhc on 2008-02-19
You can also set up evolution to work with gmail.

---

### Post by mainstreetexile on 2008-04-15
Golem, thanks for the heads up on the bash code, it works great!

The only tweak I had to do to get this working for mailto links clicked in Firefox under kubuntu was:
1) go to firefox about:config
2) add a new string named "network.protocol-handler.app.mailto" with the path to your script as the variable

---

