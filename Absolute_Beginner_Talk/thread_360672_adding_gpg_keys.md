---
title: "adding gpg keys"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by GQed76 on 2007-02-13
Ok, i alwqays fail at this....i dont think I am understanding the concept of gpg keys

For example when im told

    * Add the GPG key 
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9 ; \
gpg --export -a 0x483170E9 | sudo apt-key add -
```

Is that in the terminal?  In the sources list?  Is it one line? 2?

Whenever i go throu a walk through, I seem to get stuck at this step.  if i do the first line in the terminal nothng happens...

any advice?

---

### Post by jvc26 on 2007-02-13
You copy/paste those lines into terminal. Run the first line, then the second.
Il

---

### Post by GQed76 on 2007-02-13
then that server must be down....nothing happens in terminal.. i havent been able to get Beryl to work....so i was gonna try compiz

*sigh*

---

### Post by jvc26 on 2007-02-13
nope you're wrong bout the server I just noticed :) The code is wrong: Replace the first line with this:
```

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9 ;

```
That should work for you just worked for me now :)
Il

---

### Post by muguwmp67 on 2007-02-13
Is this for apt/synaptic?

You should still be able to use the repository that you've added if you can't get the key.  For obvious reasons, I'm sure this isn't recommended.  In synaptic it will give you a warning that the package you are trying to install doesn't have a verifiable key, but it will still allow you to load the package.

---

### Post by jvc26 on 2007-02-13
All's well - there was an error in the code as it had the \ at the end of the line, take it out and the code worked fine for me :)
Il

---

### Post by GQed76 on 2007-02-13
thanks for the help, i removed the /  when i hit enter i just get
gpg: requesting key 483170E9 from hkp server wwwkeys.eu.pgp.net
with a flashing cursor

---

