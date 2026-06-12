---
title: "New to linux need help getting started."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by mrpilot007 on 2007-12-01
I've been a pc user for years and I've known about linux for awhile but I am absolutely clueless where to start. I thought I could do it but I cant even get one file to run. I wanted to update my video card drivers but it says I must run from root. I'm not so sure this is the absolute beginning users section since I am obviously a preconception user to linux (if that makes sense. trying to find something more noobish than absolute zero lol)

Thanks for any help. Tell me where to start with getting familiar with managing a linux installation. :confused:

---

### Post by ptn107 on 2007-12-01
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) - try the links in the "Getting Help" section to familiarize yourself.

Any questions just ask on the forums here, it will get answered.

---

### Post by mrpilot007 on 2007-12-01
OK thanks. I'll start there.

---

### Post by r4ik on 2007-12-01
Hi welcome,

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

just some links.


Good luck !

---

### Post by stoodleysnow on 2007-12-01
What they said.:lolflag:

---

### Post by XVII on 2007-12-01
Beef up on knowledge is my only advice.  [Free Linux Books]("http://www.linux-books.us/linux_general.php").

---

### Post by fatality_uk on 2007-12-01
> **stoodleysnow said:**
> What they said.:lolflag:

What he SAID ^^_____^^ too :lolflag:

To be honest, the best way to approach most of the new Linux distros (releases) Ubuntu, Fedora et al, if your moving away from Windows, is use the GUI to configure most of the things you need. With Ubuntu, it's VERY easy to get a LOT of the stuff you want from the "Add/Remove..." menu item in Ubuntu. Look for info about enabling software sources: "System->Administration->Software Sources". You will need to just click a few checkboxes to save a LOT of hassle.

Once your happy with the basic setup of you shiny new Ubuntu box, then please take time to learn about using the terminal. It's got a million and 1 uses, all good and really allows very fine tuning of your system, right down to the core (Kernel). There will be times when you NEED to use it to install software, application that are a single binary file such as a xxxxx.run file.

Anyway, happy Linuxing :D

---

### Post by mulder_edu on 2007-12-01
The root user thing hit me when I first switched too.  Root is the Administrator, but you don't login to the Admin account like you do in Windows.  In Linux you run what is alot like the Run As function in Windows (in Vista you now have a right click option for "Run As Administrator", essentially the same idea).
The easiest way to access the Admin/root privileges is to open the Terminal (main menu -> Accessories -> Terminal, which is like the DOS prompt, of course) and type "sudo -s" (without the quotes).  It will prompt you for the root password.  This is the same as your regular login account password (another concept that M$ borrowed for Vista).  Type in your password and it will now show the user name as "root" instead of your name.  This will give you root privileges while working in the Terminal.

Check out the screen shot:

---

### Post by XVII on 2007-12-01
By the way, running as root is not advisable.

---

### Post by mulder_edu on 2007-12-01
Ah, yes.  Forgot to mention that.  Running as the root user is not something you want to do very often.

---

