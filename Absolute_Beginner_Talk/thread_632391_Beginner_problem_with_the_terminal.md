---
title: "Beginner problem with the terminal"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by HEN*K on 2007-12-05
Hi!

Simple question...

I'm trying to convert some .daa files into .iso and I've forgotten what to do if the file I'm trying to convert has a space in its file name. Let's say the file name is "Im Stupid" and i write Im Stupid.daa then the terminal thinks that Stupid is a parameter. What should I do to make it convert the file anyway. I've tried renaming the file so that it doesn't contain any spaces but since the whole thing consists of three parts then the converting stops after a third of the converting progress since it can't find the original filename to continue with (at least I suppose that's why it stops). I'm pretty sure I've managed to make the terminal ignore spaces in file names before, but I can't remember how... Can some one help me? I'd appreciate it. 

Well, at least I'mtrying to learn...

/Henke

---

### Post by kebes on 2007-12-05
> **HEN*K said:**
> Hi!
I've forgotten what to do if the file I'm trying to convert has a space in its file name.

On the commandline, you can put the filename in quotes in order to make sure it is taken as a single token. Something like:
cat "Im Stupid"

Would work. If you prefer, you can use escape sequences by using the backslash ("\") character, like so:
cat Im\ Stupid

The sequence "\ " basically means "treat this as a space in the token, not as a space between commandline elements".


Finally, a neat trick is to use the "tab autocomplete" to add those things for you. Let's say you're in a directory and want to run "cat" on that file, just type:
cat Im
And then press "tab"... the shell will autocomplete the rest of the filename for it, assuming that there are not other files that start with "Im". Basically you just write enough of the filename for the shell to distinguish it from other files, and then press tab to have it complete. This save time for filenames that have spaces and especially for long filenames.

Hope that helps.

---

### Post by HEN*K on 2007-12-05
I'm trying it now... Seems like it would work but I'm still having troubles with it... If I type like  ./poweriso convert /home/folder/subfolder/file\ file.daa -o /home/folder/subfolder/file.iso -ot iso it still says "cannot read compressed image file". Am I doing something else wrong? I'm trying to make it som that I'll be able to watch the .daa files that I got and to be able to do that I'm trying to convert them into .iso files. Is there another way or is my way of doing it the wrong way?

---

### Post by HEN*K on 2007-12-05
never mind, now it's working... the problem now is to get a hold of a program that will play iso files... i was pretty sure vlc did it but nooo...

---

### Post by HEN*K on 2007-12-05
never mind again (as if any one would). thanks for helping me get started, i figured out the rest myself. i'm now extracting the -avi files from the .iso file so i think i'm where i wanna be right now...

thanks

/henke

---

### Post by kebes on 2007-12-05
> **HEN*K said:**
> never mind again (as if any one would). thanks for helping me get started, i figured out the rest myself. i'm now extracting the -avi files from the .iso file so i think i'm where i wanna be right now...

I'm glad you got it working!

---

