---
title: "One more big mistake"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by bengar on 2006-12-23
Trying install vlc from the vlc homepage I did a big mistake, now this appear

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/B]

Then when I close that message appear this

[B]E: Type ‘[http://packages.freecontrib.org/ubuntu/plf/’](http://packages.freecontrib.org/ubuntu/plf/’) is not known on line 42 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: Type ‘[http://packages.freecontrib.org/ubuntu/plf/’](http://packages.freecontrib.org/ubuntu/plf/’) is not known on line 42 in source list /etc/apt/sources.list
E: Unable to lock the list directory[/B]

  I want to know how can erase in the line 42 because when I do it a message said **You do not have the permissions necessary to save the file.** Is a stupid question, Is using sudo su? thanks people.

The big problem is that I dont have repositories indexes.

---

### Post by taurus on 2006-12-23
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by bengar on 2006-12-23
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```



Taurus you are the man, thank you. Is running again...\\:D/


But in update manager this appear 

[B]Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/B]
What can I do, follow the sudo instruction?

---

### Post by shane2peru on 2006-12-23
Please post the results of:
```
cat /etc/apt/sources.list
``` So we can see it.

Also if you want to edit your sources.list manually you can do this:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
This will make a backup copy so if you really mess things up you can just copy this source list back to the original name.  To edit your source list put this in a terminal: ```
gksu gedit /etc/apt/sources.list
```  This will give you the ability to edit those lines.  To remove them just put a # in front of them, and the computer will see them as a comment instead of a code.  Example:

The computer sees this line as code
#the computer doesn't see this line as code, just a comment.

Shane

---

### Post by shane2peru on 2006-12-23
I guess I'm too slow!

Shane

---

### Post by taurus on 2006-12-23
```
sudo apt-get install -f
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by bengar on 2006-12-23
> **taurus said:**
> ```
sudo apt-get install -f
sudo aptitude update
sudo aptitude upgrade
```



Perfect, perfect, Taurus excellent is running again. Well you maybe kill me this is the last thing bad in my OS every time I install a program, this program appear with problem:
 **Errors were encountered while processing: mldonkey-server**, How can I unistall the mldonkey-server?

---

### Post by bengar on 2006-12-23
> **shane2peru said:**
> I guess I'm too slow!

Shane

Don't worry mi pana is better that nothing, thanks too.

---

### Post by shane2peru on 2006-12-23
Open your terminal again and type:

```
sudo apt-get remove mldonkey-server
```

Also you can open synaptic and search for it and uninstall it that way.

Shane

---

### Post by bengar on 2006-12-23
> **shane2peru said:**
> Open your terminal again and type:

```
sudo apt-get remove mldonkey-server
```

Also you can open synaptic and search for it and uninstall it that way.

Shane

I think that I did both instructions today early in the morning but I will try again, Tnxs shane2peru. I I'll reported the result.

---

