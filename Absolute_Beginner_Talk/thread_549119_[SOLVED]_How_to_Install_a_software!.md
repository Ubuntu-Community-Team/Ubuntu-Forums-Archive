---
title: "[SOLVED] How to Install a software?!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by lordfkiller on 2007-09-12
Hi there.

I've just migrated from Windows to Linux. I recently downloaded Thunderbird. But I am confused with the files. In windows, there used to be only one MSI file. That file, when executed, installed the software. But I don't see any installer file here.

Thanks for your help in advance.

---

### Post by Kobalt on 2007-09-12
You should read this : [https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html)

Welcome to Ubuntu :)

---

### Post by mcduck on 2007-09-12
[How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/") :D

---

### Post by mostwanted on 2007-09-12
> **mcduck said:**
> [How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/") :D

If you've gotta link, at least link to the original which has more translations :)

[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

---

### Post by misfitpierce on 2007-09-12
Also can get pre-done deb files ready for download click install at [http://getdeb.net](http://getdeb.net)

---

### Post by Maestro23 on 2007-09-12
One more log on the fire: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Johnny3 on 2007-09-12
Go to Applications-Add/Remove-Internet click on Thunderbird add.
Then go here to find out how to update [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)  
That is how I did it easier for me. I am a cut and paste person. Thunderbird has a good news grouper reader.
Johnny3
Gainesville Fl
Liking Ubuntu more ever day

---

### Post by lordfkiller on 2007-09-12
ubuntuzilla solves the problem only for Thunderbird, but I want to learn how to install the latest version of each software generally.

I tried Application-Add/Remove and Synaptic Package Installer, but the latest version of Thunderbird available through these was 1.*. The one I've downloaded is 2.0.0.6.
I also tried installing it manually by running sudo checkinstall. The command was not found!

Please let me know why is the version available through Add/Remove and Synaptic so old and why I can't install the software manually.

Thanks.

---

### Post by nanotube on 2007-09-12
> **lordfkiller said:**
> ubuntuzilla solves the problem only for Thunderbird, but I want to learn how to install the latest version of each software generally.

I tried Application-Add/Remove and Synaptic Package Installer, but the latest version of Thunderbird available through these was 1.*. The one I've downloaded is 2.0.0.6.
I also tried installing it manually by running sudo checkinstall. The command was not found!

Please let me know why is the version available through Add/Remove and Synaptic so old and why I can't install the software manually.

Thanks.

the ubuntuzilla site explains why the version of thunderbird in the repos is old. didn't read the site, eh? :)

and if you read the monkeyblog installation link you'd know what's up with checkinstall, too. as well as "how to install the latest version of each software generally".

so please, just read the links posted. :)

---

### Post by lordfkiller on 2007-09-12
I did read them both.

I don't understand this:

ubuntuzilla: 
[INDENT]Due to the way Ubuntu packaging system is structured, once a release of Ubuntu is made, the Firefox and Thunderbird versions are frozen, and no updates are released except for security patches (this is true for the other packages as well, not just for the Mozilla ones).[/INDENT]

and for monkeyblog article:

First I'm not sure if what I have for Thunderbird 2.0.0.6 is source code or compiled one. There IS a file that runs the software.
Assuming that it is source code, I couldn't run ./configure(No such file or directory). Nor does sudo make install(make: *** No rule to make target `install'.  Stop.). And sudo checkinstall(command not found).

---

### Post by CaptainInsaneO on 2007-09-12
You have to cd to the directory you're trying to run those from.

---

### Post by Mazza558 on 2007-09-12
The vast majority of software that most people will ever have to use is contained in the Add/Remove Programs section, in "Applications".

---

### Post by nanotube on 2007-09-12
> **lordfkiller said:**
> I did read them both.

I don't understand this:

ubuntuzilla: 
[INDENT]Due to the way Ubuntu packaging system is structured, once a release of Ubuntu is made, the Firefox and Thunderbird versions are frozen, and no updates are released except for security patches (this is true for the other packages as well, not just for the Mozilla ones).[/INDENT]

hm, i suppose that is somewhat obtusely worded... the repositories for an ubuntu release do not make major upgrades - just security fixes. when feisty was released, tb1.5 was the latest version, so now tb1.5 is what you get in the feisty repositories. i have changed the phraseology of that part on the ubuntuzilla site to (hopefully) be more clear. please review and let me know if it makes better sense now.

> 
and for monkeyblog article:

First I'm not sure if what I have for Thunderbird 2.0.0.6 is source code or compiled one. There IS a file that runs the software.
Assuming that it is source code, I couldn't run ./configure(No such file or directory). Nor does sudo make install(make: *** No rule to make target `install'.  Stop.). And sudo checkinstall(command not found).

the tar.gz from mozilla is already compiled. so you don't need to ./configure and make and all that. just extract the archive, and run the executable. 
if you want to better integrate it into the system (menu items, etc)
then you can look here:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by mcduck on 2007-09-12
> **mostwanted said:**
> If you've gotta link, at least link to the original which has more translations :)

[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

I didn't even know the original is back online again. I had that one in my link collection until it went down, and then I changed to the best working mirror available.. :)

---

### Post by sumguy231 on 2007-09-12
Edit: Never mind.

---

### Post by lordfkiller on 2007-09-13
I followed instructions at [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion), but finally I installed ubuntuzilla and used it.
Since I am used to Windows, I sometimes get confused. Because in Windows you can never run a program (though it is compiled) without installing(there ARE a few exceptions).

Thanks everyone.

---

