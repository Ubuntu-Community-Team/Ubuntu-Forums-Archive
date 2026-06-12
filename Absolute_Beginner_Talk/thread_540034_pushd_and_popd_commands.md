---
title: "pushd and popd commands"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by dwhitney67 on 2007-09-01
Does anybody know which package provides the 'pushd' and 'popd' shell commands?

Is there any option available with apt-get that allows for me to determine this?

With yum (which is a Red Hat and Fedora tool similar to apt-get), there is such a feature.  With apt-get, I can't tell.

---

### Post by wormser on 2007-09-01
With apt you use **apt-cache search** to find packages and to learn more **apt-cache show** to get the details of the package.  I think **ipopd** is the package you are looking for.

---

### Post by heimo on 2007-09-01
> **dwhitney67 said:**
> Does anybody know which package provides the 'pushd' and 'popd' shell commands?

Those are built-in commands in bash. I don't think there's a way to find this out using apt-tools, as those are not separate binaries in your system and for instance *apropos *doesn't know about those.

---

### Post by dwhitney67 on 2007-09-01
> **heimo said:**
> Those are built-in commands in bash. I don't think there's a way to find this out using apt-tools, as those are not separate binaries in your system and for instance *apropos *doesn't know about those.

Thanks for the enlightenment.  For some reason I was thinking that pushd and popd came from a separate package.  As you stated they don't... they are available with bash.  I was trying to document where I obtained these, and now I remember that I "obtained" them when I replaced the link of /bin/sh to point /usr/bin/bash (in lieu of dash).

Anyhow, thanks.

---

### Post by cmnorton on 2007-11-05
I have a shell script that came over from RedHat. I have read some posts indicating that I needed to change #!/bin/sh to #!/bin/bash. I did but my shell script still does not recognize pushd and popd.

What am I doing wrong?

Edit 11/05/07

I am supposed to install bash-builtins. I have, and will comment back here, if this solves my problem.

This is what the error looks like:

/home/ics/ics_util/DBImport: 202: pushd: not found
/home/ics/ics_util/DBImport: 209: popd: not found

---

### Post by dwhitney67 on 2007-11-05
First verify if you have bash installed on your system.  Run these commands:
```

$ ls -l /bin/bash
$ ls -l /bin/sh
```

The first command should tell you if you have bash installed.  The second command tells you whether your system has linked 'sh' with 'bash'.  Most Linux distros do this; Ubuntu does not.

If you do not have bash, get it using the apt-get command or synaptic.

If you are like me, and annoyed that Canonical decided to do something crude/different for the /bin/sh, blow away the link and set it to point to bash.  This will obviate the need to edit scripts you may obtain from the third parties.  Here's how you do that:

```
$ sudo rm -f /bin/sh
$ sudo ln -s /bin/bash /bin/sh
```

---

### Post by linuxican on 2008-06-10
> **dwhitney67 said:**
> First verify if you have bash installed on your system.  Run these commands:
```

$ ls -l /bin/bash
$ ls -l /bin/sh
```

The first command should tell you if you have bash installed.  The second command tells you whether your system has linked 'sh' with 'bash'.  Most Linux distros do this; Ubuntu does not.

If you do not have bash, get it using the apt-get command or synaptic.

If you are like me, and annoyed that Canonical decided to do something crude/different for the /bin/sh, blow away the link and set it to point to bash.  This will obviate the need to edit scripts you may obtain from the third parties.  Here's how you do that:

```
$ sudo rm -f /bin/sh
$ sudo ln -s /bin/bash /bin/sh
```
This worked.
Thanks dwhitney67

Saeed

---

### Post by Vivaldi Gloria on 2008-06-10
> **dwhitney67 said:**
> 
If you are like me, and annoyed that Canonical decided to do something crude/different for the /bin/sh, blow away the link and set it to point to bash.  This will obviate the need to edit scripts you may obtain from the third parties.  Here's how you do that:

```
$ sudo rm -f /bin/sh
$ sudo ln -s /bin/bash /bin/sh
```

The default shell is dash because it is faster. You may slow your boot time if you use bash rather than dash. I don't know actually whether there is an observable difference in boot times and I'd like to know.

But AFAIK you can use bash even if your /bin/sh links to dash. First make sure that your script starts with #!/bin/bash and it is executable. Now there is a difference between calling your script with 

```
sh script
```

and

```
./script
```

The first one uses /bin/sh which is dash and the second one uses bash.

So to start your script with bash make sure that

1) It starts with #!/bin/bash
2) It is executable
3) You call it by name rather than "sh script".

---

### Post by dwhitney67 on 2008-06-10
There are many 3rd-party scripts that begin with the "#!/bin/sh".  Do you suggest I edit each one I encounter so that it has "#!/bin/bash"?

I know, I realize that this is not an everyday problem, but still it is annoying to troubleshoot an error when a script works flawlessly on one *nix system, but not on Ubuntu.

With dash, and I believe this is how this thread got started, the commands 'pushd' and 'popd' are not available.  Similarly, a simple command like the following is also doesn't work:
```
$ cp myfile{,.bak}
```
What option do I have at my disposal when merely using the command line?  Maybe that's where supporters of dash should weigh in.

---

### Post by Vivaldi Gloria on 2008-06-10
> **dwhitney67 said:**
> There are many 3rd-party scripts that begin with the "#!/bin/sh".  Do you suggest I edit each one I encounter so that it has "#!/bin/bash"?.

Actually, that is exactly what I suggested. But I understand if you don't like it.

---

