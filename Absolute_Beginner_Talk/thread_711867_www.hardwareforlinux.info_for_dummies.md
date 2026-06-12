---
title: "www.hardwareforlinux.info for dummies"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-01
I was wondering if someone could break this site down for me. It seems as though its a site dedicated to a reference for all computer models to help people build a perfect linux-based system easier. I can't seem to to figure it out how. How do I create the file I'm suppose to upload? Perhaps we could start a thread that explains this site, from start to finish in a "for dummies" type format.

Thanks all!

Edit: Sorry, the actual name of the website is [www.hardware4linux.info](www.hardware4linux.info)

To the moderators: Can you edit the name of this thread? I would recreate it if I could delete it.

---

### Post by Crooksey on 2008-03-01
Erm...

> 
   1.  Download Hardware4Linux collector.
   2. Install Hardware4Linux collector.
   3. Run the Hardware4Linux collector on your system. As root: /opt/hardware4linux.info/bin/hwreport /tmp/report.
   4. Upload Hardware4Linux collector's generated report.
   5. Rate the components of your uploaded system.


Taken from the bottom of the page.

---

### Post by whoscheesemine on 2008-03-01
Well to be more descriptive I'm actually stuck on step 2.

Step 2 consists of three smaller steps:

   1.  apt-get install lsb
   2. apt-get install alien
   3. alien -i <package>

I entered the first one into the terminal... no problem everything installed.

I entered the second one... once again no problem it all installed just fine.

As for the third step, I know that when it comes to terminal instructions that generally when a word is in the brack symbols or "less than; greater than" symbols that it generally means that you have to replace that word with something else. Well I have no clue what I'm supposed to replace that with. Here's my log including the couple of dumb tries at the end that I KNEW weren't going to work, but figured I would try anyways.

```
shekels@MPC:~$ sudo apt-get install lsb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb is already the newest version.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-gnomevfs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
shekels@MPC:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
alien set to manual installed.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-gnomevfs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
shekels@MPC:~$ # alien -i <package>
shekels@MPC:~$ alien -i <package>
bash: syntax error near unexpected token `newline'
shekels@MPC:~$ 

```

---

