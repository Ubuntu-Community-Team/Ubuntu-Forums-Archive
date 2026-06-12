---
title: "&quot;Failed to execute child process &quot;firefox&quot; (No such file or directory)&quot;??"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-02-19
A client of mine recently broke his firefox. I don't know anything about how it happened. When you attempt to run firefox, the message in the title of this thread is presented on screen with an OK button.

I tried uninstalling and reinstalling using synaptic, but that didn't seem to work as the same error comes up.

I also tried to execute "firefox" from terminal.  It said it was a bad command.  But when I type "sudo apt-get install firefox", it says it is installed.  (See screenshot).

I've been trying to get this fixed for a week.  Can anyone help?

---

### Post by gsiliceo on 2008-02-19
it seems that it can't find in in /usr/bin/, maybe it has another name, search for it in that folder.

---

### Post by p_quarles on 2008-02-19
Perhaps the package is broken. This might explain why the system is confused about whether or not it is installed. Try fixing it:
```
sudo dpkg-reconfigure firefox
```

---

### Post by diablo75 on 2008-02-20
This didn't fix it.  (See screenshot)

---

### Post by diablo75 on 2008-02-21
Bump...  :(

---

### Post by warrior24 on 2008-02-21
I too have had this problem. but now I am having this problem. 

[http://ubuntuforums.org/showthread.php?t=703121](http://ubuntuforums.org/showthread.php?t=703121)


try reinstalling it.

---

### Post by jan de beuker on 2008-02-21
Mayby try removing it using the command  --purge and then reinstall it

---

### Post by diablo75 on 2008-02-21
> **jan de beuker said:**
> Mayby try removing it using the command  --purge and then reinstall it

What's the entire command I'll need to use?

---

### Post by gsiliceo on 2008-02-21
sudo aptitude purge firefox

If you type firefo or any word and hit tab twice in your keyboard, bash will complete de command, try that to see if its asociated to another binary.

---

### Post by diablo75 on 2008-02-21
"Install firefox through terminal or synaptic still dosen't work, same
errors.
In the screenshot I sent I had already purged it.  Then installed it, it
acted like it reinstalled the old configuration.
Purged it, tried synaptic, same error messages when trying to start
firefox."

---

### Post by gsiliceo on 2008-02-22
Using adept(sudo aptitude install adept) You can see all the files that a package installs and modifies, so you can see if something is left when purging.

---

### Post by diablo75 on 2008-02-22
Could you please make use of the code button up top and show me exactly what I'm suppose to type?

---

### Post by gsiliceo on 2008-02-22
> sudo aptitude install adept
> adept_manager
Using the search type firefox, the package named "Firefox" make click on it, and then in details. The information you will see may help you diagnose whats wrong.
Try looking at the details with firefox installed and uninstalled.
I'm just throwing rocks in the dark, but i hope this helps.

---

