---
title: "Problem with ndiswrapper"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by mikeymike1 on 2006-07-02
Hey,
I typed: 
*sudo tar zxvf /home/mike/desktop/ndiswrapper-1.19.tar.gz  *
and it worked fine.

Then I entered:
*cd /home/mike/ndiswrapper-1.19*
and it worked fine.

But when I type:
*sudo make install*
I get sudo:make: command not found.

Could someone help me out. **Kubuntu** is my first ecnounter with Linux.

Thanks,
Mike

---

### Post by Jagot on 2006-07-02
Is there any reason you're not using the version in the repo's?  You could just do:

```
sudo aptitude install ndiswrapper-utils
```

If for some reason you do need that specific version you are trying to compile, do you have build-essential installed?

Have a look here at compiling from source as you missed out a couple of stages there:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by mikeymike1 on 2006-07-02
When I typed in: 
```
sudo aptitude install ndiswrapper-utils]
```

I get:
Reading Package lists... done
Building dependency tree... done 
Initializing package states... done
Building Tag database... done
Couldn't find any package whose name or description matched "ndiswrapper-utils" No package will be installed, upgraded or removed.

So I suppose that's a problem.
I'll take a look at the link you recommended.

Thanks,
Mike

---

### Post by Agent86 on 2006-07-02
Go to the Ubuntu wiki ndiswrapper instructions at

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
Follow steps 4, 4.1, and 4.2.
Step 4.3 doesn't apply to recent ndiswrapper versions, so then you go to the ndiswrapper wiki at

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")
and follow all the steps under "Installation," beginning with "Compile and install" and through "Configure interface."

---

### Post by mikeymike1 on 2006-07-02
Also, does it matter that I'm using Kubuntu as opposed to Ubuntu. Because I see it uses Adept Manager instead of Synaptec, which seems to have packages that Adept does not. Perhaps I'm totally off base-- I am very new to this. Should I consider switching? or do they work, as advertised, exactly the same except for the different desktop interfaces.  

Thanks and sorry for the super novice questions,
Mike

---

### Post by Apple 101 on 2006-07-03
[QUOTE=Agent86]Go to the Ubuntu wiki ndiswrapper instructions at
[http://http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")
and follow all the steps under "Installation," beginning with "Compile and install" and through "Configure interface."[/QUOTE]I can't get to the ndiswrapper site at all - Error 403 Forbidden Access.  By the way, your link is wrong.

---

### Post by Agent86 on 2006-07-03
[QUOTE=Apple 101]I can't get to the ndiswrapper site at all - Error 403 Forbidden Access.  By the way, your link is wrong.[/QUOTE]Thanks. Link is fixed / changed to one that's currently working. I see that 1.19 is now stable.

And I just want to second what jagot mentioned up-thread, you don't need to compile ndiswrapper unless the version in the Ubuntu repositories doesn't do the job for your setup.

Though as far as compiling projects go, ndiswrapper is one of the easiest ones around.

---

### Post by Jagot on 2006-07-03
mikeymike1 - in your post above about trying to get ndiswrapper through aptitude you put a square bracket on the end of ndiswrapper-utils which is why it couldn't find it.  If you're still trying to get it to work then just copy what I put and try again.

---

