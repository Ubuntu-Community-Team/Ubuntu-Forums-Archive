---
title: "Need help with sudo apt-get update + &quot;paste&quot;"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-28
1. I have inserted **sudo apt-get update** into terminal and hit <enter>. I get this reply:

kittyhawk63@kittyhawk63:~$ sudo apt-get update
**E: Type '“deb' is not known on line 53 in source list /etc/apt/sources.list**
kittyhawk63@kittyhawk63:~$

BTW, **source list /etc/apt/sources.list** doesn't tell me much as a noob. What am I supposed to do with this to correct the problem?

Anyone with experience in this area is being sought.  How do I get to the line to edit it and what do I do when I get there. In other words, what do I delete or enter on line 53 in source list? And, where is source list?

2. Why can't I **copy** from terminal and **paste** directly into one of these posts? I can copy a line in terminal by right clicking, but "paste" is ghosted when I come to pasting the line into a post. I can paste the line from terminal into Text Editor. From Text Editor, I can copy the pasted line and paste into here fine. Is that normal by default? Sometimes when the "paste" is ghosted when right clicking, I can go to Edit on the Menu bar and select paste if paste is not ghosted. Sometimes it is and sometimes it is not. Weird! :confused:

Thanks for any suggestions that may resolve this.
kh

---

### Post by taurus on 2007-02-28
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the " at the beginning and the end from line 53.  Save the change and run that command again.

```
sudo aptitude update
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by kittyhawk63 on 2007-02-28
Taurus,
Thanks for the advice. I'm on my way to get it fixed. I'll post the results of your suggestion.
kh

---

### Post by kittyhawk63 on 2007-02-28
I resolved number one (1) with Taurus's suggestion. Thanks Taurus. =D>

Now to number two (2). Any suggestions there?
kh

---

### Post by petersjm on 2007-02-28
To copy something from the terminal, instead of CTRL+C, you need to highlight the text then press CTRL+SHIFT+C (same for pasting into the terminal: CTRL+SHIFT+V)

---

### Post by kittyhawk63 on 2007-02-28
> **petersjm said:**
> To copy something from the terminal, instead of CTRL+C, you need to highlight the text then press CTRL+SHIFT+C (same for pasting into the terminal: CTRL+SHIFT+V)

Petersjm,
Thanks for the advice. I am off to give it a try. I will post the results.
kh

---

### Post by kittyhawk63 on 2007-02-28
> **petersjm said:**
> To copy something from the terminal, instead of CTRL+C, you need to highlight the text then press CTRL+SHIFT+C (same for pasting into the terminal: CTRL+SHIFT+V)

Petrersjm,
The Ctrl+Shft+C copied the highlighted text in terminal. I still had to go to Menu->Edit->Paste to get the text pasted into the post. The "paste" did not show up at all by right-clicking. Is there a "paste" command with Ctrl+Shft?
I tried Ctrl+Shft+V. Nothing happend. :confused:
kh

---

### Post by v8YKxgHe on 2007-02-28
> **kittyhawk63 said:**
> Petrersjm,
The Ctrl+Shft+C copied the highlighted text in terminal. I still had to go to the Menu->Edit->Paste to get the text pasted into the post. The "paste" did not show up at all by right-clicking. Is there a "paste" command with Ctrl+Shft?
I tried Ctrl+Shft+V. Nothing happend. :confused:
kh

I normally use Shift+Insert ... or is it Ctrl? Hum! one or the other anyway! Yeah I normally use that to paste into terminal.

---

### Post by steven8 on 2007-02-28
Just use the edit>copy and edit>paste functions when in Linux.  OpenOffice and gedit handle the shortcuts which windows find common, but some programs in Linux don't.  I'm just forcing myself to use the edit>copy/paste route.  it doesn't take that much longer and works every time. :)

---

### Post by kittyhawk63 on 2007-02-28
Thanks to all for your replies. I will close the thread. 

Morning to ya Steve8! :)

kh

---

### Post by bapoumba on 2007-02-28
In complement to what has been said about copying something from the terminal to another application (like a web browser to paste in a post), just highlight the relevant text, and middle click in the other application. It will paste the currently highlighted text.
But this requires the terminal window to remain open (middle click to paste actually works from any open window to any other window, terminal included).

If you want to copy from a terminal to (the same or another) terminal window:
To copy from a terminal : SHIFT-CTRL-C
To paste in a terminal : SHIFT-CTRL-V
(because CTRL-C has a separate action in a terminal)

If you want to copy from a terminal to another window (but a terminal):
To copy from a terminal : SHIFT-CTRL-C
To paste in a web browser : CTRL-V

---

### Post by kittyhawk63 on 2007-02-28
Bapoumba,
Thanks for your input. I will give it a try. I will post my results per your instructions.
kh

> **bapoumba said:**
> In complement to what has been said about copying something from the terminal to another application (like a web browser to paste in a post), just highlight the relevant text, and middle click in the other application. It will paste the currently highlighted text.
But this requires the terminal window to remain open (middle click to paste actually works from any open window to any other window, terminal included).

If you want to copy from a terminal to (the same or another) terminal window:
To copy from a terminal : SHIFT-CTRL-C
To paste in a terminal : SHIFT-CTRL-V
(because CTRL-C has a separate action in a terminal)

If you want to copy from a terminal to another window (but a terminal):
To copy from a terminal : SHIFT-CTRL-C
To paste in a web browser : CTRL-V

---

### Post by kittyhawk63 on 2007-02-28
Bapoumba,

You're a genius! Two gold stars for your report card. Run home and tell your parents how good you were in school today.

kh

---

### Post by bapoumba on 2007-02-28
:D
Not genius at all. It's the X-clipboard.
When at work, I sometimes have to use Microsoft Windows. I always paste with middle-click (and of course, it does not work ;)).

---

### Post by steven8 on 2007-02-28
steven8@steven8-desktop:~$

Wow!  It works!!  Just pasted this from me terminal.  Thanks.  Yep, KH, we learn something new every day! :)

---

