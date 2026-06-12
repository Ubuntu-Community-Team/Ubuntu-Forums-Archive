---
title: "Extracts"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-06-30
A simple question from a noob. Can anyone tell me how to copy an error message from the Update Manager to this forum? It seems in trying to download ClamAv(?), the anti-virus program, there's been an error, partly to do with configuration. I used Synaptics to find and download the program. Posting the error message here would possibly help me - each time I used the Software Update program I'm advised of this problem, and that all installs could not be performed correctly.

I eith have to remove the downloaded portion, which hasn't installed as far as I can determine, OR make changes according to the error report (meaning another post to this forum). I've tried Ctrl-C, Ctrl-V but that doesn't work.

Any help on either topic would be appreciated.

---

### Post by forestpixie on 2007-06-30
try doing a screenshot - applications>accessories.take screenshot and attach to post

---

### Post by deadgobby on 2007-06-30
MMM it may be a problem with the repositories or some thing els.  Here is how you can copy the text. Go and open up your terminal and type in 
sudo aptitude update
 If you get an error it will tell you. Simply copy the text and post them here. All so since I was talking about repos here how you can check
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
 It will open up the sources list and give your listings. You can copy then and post them too.
Or you can use the terminal and try to install it type in 
sudo aptitude install clamav
Gobby

---

