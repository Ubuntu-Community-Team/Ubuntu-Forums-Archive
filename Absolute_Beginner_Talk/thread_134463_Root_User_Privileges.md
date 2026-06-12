---
title: "Root User Privileges"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by jfh on 2006-02-21
I installed VM Player and its Browser Appliance (which included Ubuntu), and I have finally managed to get Automagix and Firestarter downloaded and installed, but when I try to open Firestarter, I get a message telling me that I couldn't use it because I didn't have Root User Privileges.  How do I log on as a root user? I have tried the sudo command but guess I don't understand how to use it.
I have read (and printed out) Kyral's "Terminal for Beginners", and may someday understand how to use the Terminal.  Long ago, of course, I  made a deliberate effort to forget about DOS (maybe that's my problem).
 I have never used any browser but Opera, so was glad to be able to use Automagix to download it.  The Wand feature alone makes it superior to any other browser.
Thanks for any help on the root user thing. jfh

---

### Post by taurus on 2006-02-21
Assuming that you log in as the user that you've created during the installing process, then you should be able to run everything with "sudo" in front of the command.  To make sure you belong to group adm, type this at the prompt (from a terminal) and see if group adm is on that list,

id

If it is, then you are all set...

sudo firestarter

---

### Post by abhaysahai on 2006-02-22
[QUOTE=jfh]I installed VM Player and its Browser Appliance (which included Ubuntu), and I have finally managed to get Automagix and Firestarter downloaded and installed, but when I try to open Firestarter, I get a message telling me that I couldn't use it because I didn't have Root User Privileges.  How do I log on as a root user? I have tried the sudo command but guess I don't understand how to use it.
I have read (and printed out) Kyral's "Terminal for Beginners", and may someday understand how to use the Terminal.  Long ago, of course, I  made a deliberate effort to forget about DOS (maybe that's my problem).
 I have never used any browser but Opera, so was glad to be able to use Automagix to download it.  The Wand feature alone makes it superior to any other browser.
Thanks for any help on the root user thing. jfh[/QUOTE]

sudo Firestarter 
< your password>

---

### Post by jfh on 2006-02-22
In Terminal, I typed in id and in with lots of other symbols I got something that included <adm> in it.  I then syped in <sudo firestarter> and the Firestarter screen came up.  I configured it by largely leaving the defaults enabled, and finally got a Firestarter icon on the desktop, but when I r.c. on it I get an error message telling me: "Failed to execute child process '/home/vmware/firestarter.8'(Permission denied)".  I tried to look up "child process" in Scroogle, and got lots of stuff, none of which I understood.  What should I do now to activate Firestarter?

---

