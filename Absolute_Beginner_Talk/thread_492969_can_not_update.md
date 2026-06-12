---
title: "can not update"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by tking on 2007-07-05
can not update ubuntu from ubuntu  like as if the server is down? any ideals.

---

### Post by Seisen on 2007-07-05
Can you post the errors you are getting and post your source list. Also can you browse the web?

---

### Post by lisati on 2007-07-05
You might try another server. Keep in mind that the nearest isn't always the best. On the "system" menu, under the "Administration" option, you will find "software sources". Click on the button by "Download From", and choose "other". Then click on "Select best server". Your system will then check all the servers it knows about, and try to find the one with the best connection. This might take a few minutes. If you're happy with the choice of server, click on "choose server" then "close".

---

### Post by tking on 2007-07-05
not sure how to do any of that. I want to look for update for ubuntu its self so i can install skype.

---

### Post by Seisen on 2007-07-05
To access your source list do this in the terminal. To open the terminal go to Applications>Accessories>Terminal

```
gksudo gedit /etc/apt/sources.list
```

Before you do that in the terminal do this

```
sudo apt-get update
``` then just copy and paste what is says.

---

### Post by lisati on 2007-07-05
To install skype, you will need to go to [www.skype.com](www.skype.com) then click on the "download" button next to the "home" button at the top of the web page. There's a version there for "Feisty" (Ubuntu 7.04) - download that and save to disk. When the download is complete, click on "open" in the download window to install skype. It will guide you through the process.

---

