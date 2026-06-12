---
title: "Messed up dependencies, need help"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by dreamsINdigital on 2006-03-31
Hello I'm a new Linux user.  I tried to install the new Guifications 2.13beta3 from a .deb, but i got dependencie errors.  Okay so then I thought I would try to install some of the dependencies.  I tried to update libcairo2 from a .deb, but I got more errors.  I tried to fix that through Synaptic, but it wants to remove over 100 packages.  What do I do now? :-k 

Thanks

---

### Post by Mustard on 2006-03-31
Where did you get the .deb's from?  
Do you have any record of these errors you found along the way?  
Can we see the error message you are getting now?

---

### Post by dreamsINdigital on 2006-03-31
I got the .debs here:  [http://www.ubuntuforums.org/showthread.php?t=152457](http://www.ubuntuforums.org/showthread.php?t=152457)

This is the error I got when trying to update libcairo2.

> Preparing to replace libcairo2 1.0.2-3 (using libcairo2_1.0.2-3_i386.deb) ...
Unpacking replacement libcairo2 ...
dpkg: dependency problems prevent configuration of libcairo2:
 libcairo2 depends on libxrender1 (>> 1:0.9.0-1); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing libcairo2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairo2


When I open up Synaptic, it tells me 2 packages are broken:  gaim-guifications and libcairo2.  When I try to fix one or the other, it wants to remove 189 packages, which I would rather not do.  I want to just remove the messed up libcairo2 and guifications and go back to the old ones.

---

### Post by Mustard on 2006-03-31
Is libcairo2_1.0.2-3_i386.deb the only dependency you have tried to install from dapper?

It does look like you've created a mess. :)  I'm not even sure I know the answer to this. I suppose it's too late to say that using dapper .debs in a Breezy install is a potential nightmare unless you know what you are doing.

---

### Post by dreamsINdigital on 2006-03-31
That's a dapper dependency? :-k Yes it's the only one I've tried.  I didn't know, all I was trying to do was install the new Guifications. ](*,) 

What did I do wrong to get in this mess? :confused:

---

### Post by Mustard on 2006-03-31
[QUOTE=dreamsINdigital]That's a dapper dependency? :-k Yes it's the only one I've tried.  I didn't know, all I was trying to do was install the new Guifications. ](*,) 

What did I do wrong to get in this mess? :confused:[/QUOTE]

From what I can see you got into this issue by not noticing that the thread you were reading is in the Dapper Drake development forum, and the people doing this are all running Dapper Drake, not Breezy Badger.

-edit-

Just thinking about the problem, I think you need to reinstall the old version of libcairo.

Uninstalling the latest version you have is going to leave a lot of packages with no libcairo version at all installed.  So somehow you need to reinstall the old version without removing the new version first.  If that is at all possible.

---

### Post by Mustard on 2006-03-31
I have no idea what the implications of this are going to be, but I think if you were to go into synaptic, find the old version of libcairo2, and use a force version option on it, it would install the old version. Then you might be able to unistall the Dapper version (or it might do this itself). Now I would say again that I don't know for sure whether this is going to be a messy process or a clean process.  It's up to you if you want to take a shot at it.  Feel free to talk it over some more before attempting it.

---

### Post by trent dillman on 2006-03-31
um, you could try

```
sudo apt-get -f install
```

But I don't know if that'll fix it or just try to uninstall stuff.

Of course, you could also just uninstall all that stuff then reinstall it, as long as 'apt' isn't in that list...

---

### Post by dreamsINdigital on 2006-03-31
[QUOTE=Mustard]From what I can see you got into this issue by not noticing that the thread you were reading is in the Dapper Drake development forum, and the people doing this are all running Dapper Drake, not Breezy Badger.[/QUOTE]
D'oh! 

[QUOTE=trent dillman]um, you could try

```
sudo apt-get -f install
```

But I don't know if that'll fix it or just try to uninstall stuff.

Of course, you could also just uninstall all that stuff then reinstall it, as long as 'apt' isn't in that list...[/QUOTE]
I took a look that before, but that would just uninstall stuff.

[QUOTE=Mustard]I have no idea what the implications of this are going to be, but I think if you were to go into synaptic, find the old version of libcairo2, and use a force version option on it, it would install the old version. Then you might be able to unistall the Dapper version (or it might do this itself). Now I would say again that I don't know for sure whether this is going to be a messy process or a clean process.  It's up to you if you want to take a shot at it.  Feel free to talk it over some more before attempting it.[/QUOTE]
Forcing downgrade worked! Thanks! =D>

---

### Post by Mustard on 2006-03-31
[QUOTE=dreamsINdigital]Forcing downgrade worked! Thanks! =D>[/QUOTE]

I'm pleased to hear that. :)

---

