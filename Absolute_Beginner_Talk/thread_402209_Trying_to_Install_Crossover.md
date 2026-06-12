---
title: "Trying to Install Crossover"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2007-04-05
I downloaded Crossover Demo.  But I don't know how to install it.  It ends with a .sh that is dot sh.  So could anyone tell this newbie how to install this?  Also is there a place on the site where I could get get some of the most common used if not all commands for Ubuntu?

---

### Post by badhat on 2007-04-05
```
sh install-crossover-standard-demo-6.0.1.sh
```

---

### Post by badhat on 2007-04-05
About your second question: I have not seen any list of common commands on the Ubuntu pages, but that wouldn't be the first place to look anyway, since shell commands will be about the same on any distro.  

If you Google "common linux commands" or "common unix commands" you find plenty of nice lists and tables.

---

### Post by NikoC on 2007-04-05
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

---

### Post by Wiebelhaus on 2007-04-05
> **NikoC said:**
> [http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

nice link! thanks.

---

### Post by Maestro23 on 2007-04-05
From the Crossover site: [http://www.codeweavers.com/support/docs/crossover-standard/install](http://www.codeweavers.com/support/docs/crossover-standard/install)

Other Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by waspinagermanhelmet on 2007-04-10
I tried the code from the site in a terminal... 

sudo sh install-crossover-standard-demo-6.0.1beta1.sh

I couldn't get it to install... any ideas?

---

### Post by zvacet on 2007-04-10
Where did you downloaded?Maybe on desktop.If I´m right just change directory
```
cd Desktop
```

or any other where you download it.After that run the command.

---

### Post by marianlibrarian on 2007-04-11
sh install-crossover-pro-6.0.1beta1.sh

Does NOT work! I paid for the pro version. The instructions on the crossover site say if you have the demo installed, all you have to do is type in your email and password and it will "register" the thing for you. However, what they DON'T say is that the demo is standard. And if you do the registration from the demo you only have standard even if you PAY for pro.

So I submitted a "ticket" and waited and waited and... anyway the next day I get an answer.

Uninstall the demo and then install the pro.

Did that and guess what......

The same error.

sh install-crossover-pro-6.0.1beta1.sh

no such file found.

oh joy. now i have NOTHING. I have submitted another "ticket" and now I get to wait wait wait wait....

So I came here and find the same line of code
sh install-crossover-pro-6.0.1beta1.sh

Yes --- I am logged in and
Yes --- I am at the terminal window with the little $ 
sh install-crossover-pro-6.0.1beta1.sh 
sh: install-crossover-pro-6.0.1beta1.sh: No such file or directory

Yes --- I downloaded it (it is in /tmp and on the desktop - so why the hello won't it install???

---

### Post by justin whitaker on 2007-04-11
> **marianlibrarian said:**
> sh install-crossover-pro-6.0.1beta1.sh

Does NOT work! I paid for the pro version. The instructions on the crossover site say if you have the demo installed, all you have to do is type in your email and password and it will "register" the thing for you. However, what they DON'T say is that the demo is standard. And if you do the registration from the demo you only have standard even if you PAY for pro.

So I submitted a "ticket" and waited and waited and... anyway the next day I get an answer.

Uninstall the demo and then install the pro.

Did that and guess what......

The same error.

sh install-crossover-pro-6.0.1beta1.sh

no such file found.

oh joy. now i have NOTHING. I have submitted another "ticket" and now I get to wait wait wait wait....

So I came here and find the same line of code
sh install-crossover-pro-6.0.1beta1.sh

Yes --- I am logged in and
Yes --- I am at the terminal window with the little $ 
sh install-crossover-pro-6.0.1beta1.sh 
sh: install-crossover-pro-6.0.1beta1.sh: No such file or directory

Yes --- I downloaded it (it is in /tmp and on the desktop - so why the hello won't it install???

My guess is, you did not delete the hidden files. Is the directory still there when you view hidden files in /Home?

---

### Post by marianlibrarian on 2007-04-11
Okay, you will love this...

The command on their instructions on their website is...
$ sh install-crossover-pro-6.0.1beta1.sh

I have installed many things from the terminal window and was about to go INSANE!

When it hit me. I knew I was in the right place /tmp/ and I was looking right at the file and then I saw it...

The file name...
install-crossover-pro-6.0.1.sh

$ sh install-crossover-pro-6.0.1.sh     Works!

I have posted another "ticket" telling them to UPDATE their instructions for those of us who really read them! :)

---

