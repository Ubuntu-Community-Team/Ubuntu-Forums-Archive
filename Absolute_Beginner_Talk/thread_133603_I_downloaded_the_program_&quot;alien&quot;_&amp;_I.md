---
title: "I downloaded the program &quot;alien&quot; &amp; I can NOT see its Files"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-20
Hello all !!!

I went inside "Synaptic" & under "Settings\Preferences\Files", I pressed the button "Delete cached package files".

I went inside "Synaptic", downloaded "alien" (but NO install option), but I can NOT see its files.

I went inside "/var/cache/apt/archives" & there is nothing in there.

Then I downloaded the files again.

Where can these files be?

Please Help !!!

---

### Post by nik on 2006-02-20
[QUOTE=dvarsam]Hello all !!!
I went inside "Synaptic", downloaded "alien" (but NO install option), but I can NOT see its files.
[/QUOTE]
What do you mean with no install option? Just click the program in synaptic, select "mark for installation" and click apply...

---

### Post by az on 2006-02-20
I beleive that alien in on the install cd - which is a local repository.  If the version of alien on the cd is the same one as on the online repos, then it will not download it - just use the one on the cd. 

If you actually told it to install, it would prompt you for your cd.

You can either copy the file from the cd (look in the pool/a/alien directory) or disable the cd as a repo, update and then try again.

---

### Post by dvarsam on 2006-02-20
[QUOTE=azz]I beleive that alien in on the install cd - which is a local repository.  If the version of alien on the cd is the same one as on the online repos, then it will not download it - just use the one on the cd. 

If you actually told it to install, it would prompt you for your cd.

You can either copy the file from the cd (look in the pool/a/alien directory) or disable the cd as a repo, update and then try again.[/QUOTE]

How can I disable the CD as a Repo?

---

### Post by aysiu on 2006-02-20
[QUOTE=dvarsam]How can I disable the CD as a Repo?[/QUOTE] Go to System > 
Administration > Synaptic Package Manager > Settings > Repositories and uncheck the first box.

---

### Post by dvarsam on 2006-02-20
[QUOTE=aysiu]Go to System > 
Administration > Synaptic Package Manager > Settings > Repositories and uncheck the first box.[/QUOTE]

And how do I run "alien"?

Cause I pressed "Alt+F2" & typed "alien" & I got nothing...

---

### Post by paxmaster on 2006-02-20
I am not understanding your question 

ok how about uncomment the sources in your /etc/apt/sources.list 
and run this command apt-get update 
and now run apt-get install alien 
please show the output of the command 
now do this type this updatedb 
after it finish now turn this 
whereis alien 
alien: /usr/bin/alien /usr/bin/X11/alien /usr/share/alien /usr/share/man/man1/alien.1p.gz
if the command don't work try this locate alien 

the /usr/bin/alien/ is the program maybe this not in your path if so run this /usr/bin/alien

---

### Post by cwaldbieser on 2006-02-20
[QUOTE=dvarsam]And how do I run "alien"?

Cause I pressed "Alt+F2" & typed "alien" & I got nothing...[/QUOTE]
The alien program runs in a terminal-- running it in the run box will be like running the "clear" in the run box-- it won't really do anything.

You have to type something like:
```

$ alien --to-deb myfile.rpm

```

---

