---
title: "Further adventures on the way to installing my nVidia driver..."
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-02-01
Right after the license agreement in the driver installation script, I got the following message:
[QUOTE=installer script]gcc-version-ceck failed:

You appear to be compiling the NVidia kernel module with a different compiler than the one that was used to compile the running kernel.  The linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match the version used to build the running kernel.  The compiler used to compile the running kernel was gcc 3.4; the current version is gcc 4.0.

If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation.  Otherwise, select "Yes" to abort the installation, set the CC environment variable to the name of the compiler used to compile your kernal, and restart installation.  Abort now?

Y/N[/QUOTE]
As I manifestly do not know what I am doing, I took its advice and selected Yes.  So I guess my question is, How do I change said variable?

---

### Post by Sutekh on 2006-02-01
Say 'yes'.  At the command line use
```

CC=gcc-3.4
export CC
```
and then re-run the installation script.  

[Edit: This is not right (You may need to use sudo with the export command)]

Double-check that gcc-3.4 is installed before trying this too
```

sudo apt-get install gcc-3.4
```

---

### Post by TeeAhr1 on 2006-02-01
Great, thanks!

<dumb question>
Should I change the value back to 4.0 when I'm done?
</dumb question>

---

### Post by Sutekh on 2006-02-01
You know I have no idea.  I don't *think* it does, but once you're done try 'gcc-version' and see what is says.

---

### Post by TeeAhr1 on 2006-02-01
When I try to export, I am told that there is no such command.

---

### Post by Sutekh on 2006-02-01
Did you install gcc-3.4 before trying to export?

---

### Post by TeeAhr1 on 2006-02-01
Looking again, I noticed that I did add gcc-3.4, but not g++3.4.  :-k Did I install the wrong package?  The message I got said gcc-3.4, so I'd think not...

---

### Post by Sutekh on 2006-02-01
No you shouldn't need to, the NVIDIA installer wants gcc not g++

I'm not sure why export doesn't work, paste the error here?

I think I've seen a command to force it to use gcc-4.0, but I don't know if that will cause problems.

---

### Post by TeeAhr1 on 2006-02-01
[QUOTE=error]sudo: export: command not found
[/QUOTE]
Seeing that *sudo* there got me thinking, though.  I tried *export CC* without sudo, and didn't get an error.  I'll be right back...

---

### Post by TeeAhr1 on 2006-02-02
CASE CLOSED: See this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=75074") (method 2) to see howto.  And this is exactly what I get for not searching thoroughly beforehand.

You were totally correct in everything you advised, and I appreciate the help in getting me at least halfway there.  The missing piece of the puzzle was that you can't use *sudo* with *export*.  You have to set the root password and use *su*.  (I guess.  But if anyone can tell me why that's so, I'm curious.)

---

### Post by Sutekh on 2006-02-02
[QUOTE=TeeAhr1]CASE CLOSED: See this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=75074") (method 2) to see howto.  And this is exactly what I get for not searching thoroughly beforehand.[/QUOTE]
Ahh is there anything as sweet as resolution?


[QUOTE=TeeAhr1]
You were totally correct in everything you advised, and I appreciate the help in getting me at least halfway there.  The missing piece of the puzzle was that you can't use *sudo* with *export*.  You have to set the root password and use *su*.  (I guess.  But if anyone can tell me why that's so, I'm curious.)[/QUOTE]
Yeah, only half-correct! :( 

But we both learnt something.  I'm not sure why you use 'su' rather than 'sudo' though.

---

