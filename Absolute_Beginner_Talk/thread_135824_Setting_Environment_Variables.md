---
title: "Setting Environment Variables"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by Mike_SMD on 2006-02-24
Hello everybody,
Well... after having all of my other foolish questions answered so courteously I figure that it's about time to try one more.

Can anyone tell me how I find out what the environment variable setting for my web browser is? I'm trying to donate some spare computer clicks to a distributed computing project centered on modelling climate change and whenever I try to see my contribution using the graphical manager I get the following message:

"... BOINC manager tried to display the web page, but couldn't find a web browser. To fix this set the environment variable BROWSER to the path of your web browser, then restart yadda yadda yadda ..."

Typing echo $PATH in terminal gives me the following result but I don't see a heading called BROWSER anywhere... am I on the right track with this? Can anyone tell me how to determine this value and then modify it?

mike@ubuntu:~/Climate/bbcclimate$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

Thanks very much and I really do appreciate the help!

Linux for almost three weeks now, and only had to boot up XP once to accomplish a task that I just couldn't otherwise figure out how to do... might not sound like much but I'm impressed.

Take care,


Mike_SMD.

---

### Post by Stormy Eyes on 2006-02-24
Open a terminal and type the following:

```
gedit ~/.bashrc
```

Now add the following to a blank line:

```
export BROWSER=/usr/bin/firefox
```

Now save, close the editor, and logout. When you login, the $BROWSER variable should point to /usr/bin/firefox.

---

### Post by Mike_SMD on 2006-02-24
Perfect!

That worked like a charm!

Thanks!


Mike_SMD.

---

