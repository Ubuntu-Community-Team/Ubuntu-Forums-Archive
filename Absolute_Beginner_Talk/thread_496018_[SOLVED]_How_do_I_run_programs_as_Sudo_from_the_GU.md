---
title: "[SOLVED] How do I run programs as Sudo from the GUI"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by jeffrla on 2007-07-08
Hi all,

I was wondering about running programs as a regular user and as "Sudo".  I understand that from the Terminal you run a program by using "Sudo" before the command.

My question is how do you run a program or script as Sudo from the GUI?  You can double click on it and it will ask if you want to run in a terminal, but does not give you the chance to specify to run as the regulare user or as Sudo.

Thanks,

Jeff

---

### Post by niteshifter on 2007-07-08
Well, there's gksudo ... If you have a GUI app that needs to be run as root you can wrap it in a script:

```
gksudo program-name
```

Then, when you double-click on it a password dialog will pop, you enter password, if valid password then program runs.

You can specifiy which user also, the manual page gives details (man gksudo in a terminal).

---

### Post by jeffrla on 2007-07-08
Hello,

Thx for the quick response. 

The problem I am running into is this.  I am trying to install Adobe Reader.  I downloaded the GZ file, got it extracted, I run the INSTALL from the GUI and it asks if I wan to run in a Terminal.  I click run in Terminal. it runs, asks for the location to install (/usr/local/Adobe/Acrobat7.0).  It comes back and says the folder does not exist and do I want o create it?  I say yes, then it comes back and says permission denied.

I thought...OK, I will run it from the CLI as Sudo in the folder, but it comes back and says it cannot find INSTALL.  I do an LS and it is there, but will not run.

Thanks,

Jeff

---

### Post by Bachstelze on 2007-07-08
```
sudo ./INSTALL
```

---

### Post by aysiu on 2007-07-08
**Step 1**: Delete the .tar.gz file. You don't need it.

**Step 2**: Follow [these instructions to add the Medibuntu software repositories](http://medibuntu.sos-sts.com/repository.php).

**Step 3**: Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
sudo apt-get install acroread
```

**Step 4**: Read more [about installing software](http://www.psychocats.net/ubuntu/installingsoftware)

*Optional*
**Step 5**: Consider using Evince or KPDF. Acrobat Reader is slow to load and offers little added functionality over the default PDF readers.

---

### Post by jeffrla on 2007-07-08
Thank you to all!!!

You guys and gals ROCK!!

I am so glad to see this kind of support.  Hopefully Dell will have helped push Linux ahead.  With this kind of support MS should look out.  I know it will be some time to come, but I sure like the way things are going.

Thanks you again.

Take care,

Jeff

---

