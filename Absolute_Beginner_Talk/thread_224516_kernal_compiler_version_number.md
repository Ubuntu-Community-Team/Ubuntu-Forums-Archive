---
title: "kernal compiler version number"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by wog on 2006-07-28
Is there an easy way to find out what version the compiler was which compiled my kernal?

---

### Post by ovimunt on 2006-07-28
This is probably not what you asked but just in case...

This is how you find out the version of your kernel:

```

uname -r

```

---

### Post by rowanparker on 2006-07-28
Edit: Ooops, ovimunt beat me to it :(

---

### Post by hw-tph on 2006-07-28
**uname -r** will print the kernel revision, nothing about what compiler was used.

For detailed information, **cat /proc/version** will tell you it all.

---

### Post by wog on 2006-07-28
> **ovimunt said:**
> This is probably not what you asked but just in case...

This is how you find out the version of your kernel:

```

uname -r

```

You are correct. This is not what I want to know. :)

Besides, this information is also in the Synaptic kernal listing.

The actual problem is I keep running into programs that, to install them, want something to do with the version number of compiler that was used to compile my kernal.

The current program wants the headers for the proper version of the kernal compiler, but if I don't know what version of compiler was used to make the current kernal, I can't be certain I have those headers.

Gee, that sounds so much like a tongue twister. :)

---

### Post by wog on 2006-07-28
> **hw-tph said:**
> **uname -r** will print the kernel revision, nothing about what compiler was used.

For detailed information, **cat /proc/version** will tell you it all.

Oooo, you are brilliant! The above cat command string worked. :)

Now to find those headers...

---

### Post by hw-tph on 2006-07-28
When compiling a kernel module you need to use the same compiler as was used when compiling the kernel itself. To do this, install the version of the compiler that was used and then specify the compiler using the $CC environment variable, like this:
```
export CC=/usr/bin/gcc-3.4
```
That would set the compiler to gcc-3.4 (it's available in the main repository).

Håkan

---

### Post by wog on 2006-07-28
The headers were found in the development section. 

Thank you all, I think this matter is solved. :)

---

### Post by wog on 2006-07-28
> **hw-tph said:**
> When compiling a kernel module you need to use the same compiler as was used when compiling the kernel itself. To do this, install the version of the compiler that was used and then specify the compiler using the $CC environment variable, like this:
```
export CC=/usr/bin/gcc-3.4
```
That would set the compiler to gcc-3.4 (it's available in the main repository).

Håkan

Does export get the current value out, or does it put the new value in?

EDIT: How do I find out what the current value is for an environment variable?

---

### Post by wog on 2006-07-28
How do I find out what the current value is for an environment variable?

---

### Post by hw-tph on 2006-07-28
The export command makes an environment variable available to the current shell and all subsequent subshells created from it. You can also specify environment variables for one command only (temporarily change or set a variable) by putting it on the same line as the command without "export":

```
CC=/usr/bin/gcc-4.0 ./configure
```

To see what an environment variable is set to, simply echo it. When referring to shell/environment variables you prefix a dollar sign, but you don't use that dollar sign when setting variables:

```
echo $CC
export MYVARIABLE="I am a geek"
echo $MYVARIABLE
```

Also the **env** and **set** commands will show you shell and environment variables. Hope that helps a bit.


Håkan

---

### Post by wog on 2006-07-28
> **hw-tph said:**
> The export command makes an environment variable available to the current shell and all subsequent subshells created from it. You can also specify environment variables for one command only (temporarily change or set a variable) by putting it on the same line as the command without "export":

```
CC=/usr/bin/gcc-4.0 ./configure
```

To see what an environment variable is set to, simply echo it. When referring to shell/environment variables you prefix a dollar sign, but you don't use that dollar sign when setting variables:

```
echo $CC
export MYVARIABLE="I am a geek"
echo $MYVARIABLE
```

Also the **env** and **set** commands will show you shell and environment variables. Hope that helps a bit.


It does help!

Previously I tried set, but got back a bunch of scripting code I couldn't figure out. env is much more what I was looking for.

Thank you! :)

---

