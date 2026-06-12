---
title: "Cowbell"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2007-05-05
I installed cowbell but when I try to run it I get the following:

[COLOR="Teal"]dunklegend@dunklegend-desktop:~$ cowbell

** (/usr/lib/cowbell/cowbell.exe:570): WARNING **: The following assembly referenced from /usr/lib/cowbell/cowbell.exe could not be loaded:
     Assembly:   glib-sharp    (assemblyref_index=4)
     Version:    2.10.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/cowbell).


** (/usr/lib/cowbell/cowbell.exe:570): WARNING **: Could not load file or assembly 'glib-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.ArgumentException: Invalid sequence in conversion input
Parameter name: string
  at <0x00000> <unknown method>
  at Cowbell.Runtime.Main (System.String[] args) [0x00000] 
[/COLOR]

Can somebody tell me what the problem is, and how can I solve it?

Thanks in advance

---

### Post by DSn0wMan on 2007-05-05
It looks like you need a library called glib-sharp. It is possibly part of Mono by the looks of your error. I would read the requirements of cowbell, and make sure you have all the dependencies installed.

I see that cowbell is in the repositories. Did you install it with aptitude?

---

### Post by dunklegend on 2007-05-05
I installed with aptitude, with synaptic, and with the .deb file, and none of them worked:confused:

---

### Post by dunklegend on 2007-05-05
How do I know if I have all the dependencies?

I really want to get cowbell working to see if it is what I need.

In windows I use Musicmatch Jukebox to get the album artwork, rename files, add lyrics, lookup the correct song names etc.

Is there a similar program in Ubuntu?

If there is not, how can I install Musicmatch with wine?

Thanks in advance

---

### Post by DSn0wMan on 2007-05-06
If you installed it with aptitude or synaptic you probably have all the dependencies. The only thing I can think of is that cowbell is looking for glib-sharp in a directory where it does not exist.

Maybe you could find where glib-sharp is on your computer, and add that directory to the MONO_PATH environment variable that is mentioned in your error message. It would look something like this.

```
export MONO_PATH=$MONO_PATH:/path/to/glib-sharp
```

If it works, then you need to find where MONO_PATH is defined, because the export statement will only define it for you current session.

---

### Post by dunklegend on 2007-05-11
How do I find out where glib-sharp is?

---

### Post by dunklegend on 2007-06-06
I had to format my hard drive, I installed Ubuntu from scratch, I installed cowbell with:

sudo aptitude install cowbell

and then it worked!

I don't know what changed but it's working now.

:KS

---

### Post by flickerfly on 2008-02-13
Could you echo $MONO_PATH for me? I'm having trouble with MONO_PATH also.

---

