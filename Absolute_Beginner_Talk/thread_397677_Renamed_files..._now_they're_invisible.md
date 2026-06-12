---
title: "Renamed files... now they're invisible"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by FITorion on 2007-03-30
I had a file

Hack Dusk

I renamed it .Hack\\Dusk

Now it's invisible

When into terminal to try and rename it

```

mv .Hack\\Dusk Hack\\Dusk
mv: cannot stat `.Hack\\Dusk': No such file or directory
```

HELP:(

---

### Post by cowlip on 2007-03-30
.

---

### Post by brennydoogles on 2007-03-31
> **FITorion said:**
> I had a file

Hack Dusk

I renamed it .Hack\\Dusk

Now it's invisible

When into terminal to try and rename it

```

mv .Hack\\Dusk Hack\\Dusk
mv: cannot stat `.Hack\\Dusk': No such file or directory
```

HELP:(

If you enter the folder where you created it and hit Ctrl+H all of the hidden files will be shown. In linux a file or folder is made hidden by beginning the name with a period.

---

### Post by johnc4510 on 2007-03-31
Anytime you put a . in front of a file name, it becomes a hidden file.
To see it do this:

Ctrl+ h

That will show your hidden files
Also in your home folder you can to this:

Click on view and put a check mark in the box for Show Hidden Files

---

### Post by FITorion on 2007-03-31
thanks guys I was freaking out about this

I fixed it


before I did though... ls -al showed it...  I did that before I tried mv to make sure it was still there...  which is why mv not working freaked me out

---

### Post by cowlip on 2007-03-31
.

---

