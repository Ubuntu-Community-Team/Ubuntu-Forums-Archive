---
title: "How to open a terminal"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by hippobottomus on 2006-04-17
After hours of browsing, ](*,)  (newbie) I've finally sussed that a terminal is needed to run scripts or commands. 

Qs:

1) Where do I find the Terminal program?

2) Must I create script files, before running them, and if so, where do I create them?

3) If the answer to 2) is yes, how do I create script files.

Replies to these probably dumbo Qs much appreciated!

---

### Post by croak77 on 2006-04-17
Gnome-Terminal should be in your menu. You can also pres Alt-F2 to open a run dialog. Then just type in gnome-terminal.

---

### Post by taurus on 2006-04-17
1.  Click on Applications -> Accessories -> Terminal.

2.  Yes, you need to create a script first if you want to run it!!!

3.  What exactly do you want to run?  Here is a basic one so you can get a taste of it.  At the prompt or terminal (from Step 1), type
```

gedit test.sh

```
Now, type in these lines and save it...
```

#!/bin/bash
echo "My first script..."

```
Then, you need to change the permission so you can execute it so type these two commands from the prompt again.
```

chmod 755 test.sh  <-- change the permission before you execute it
./test.sh  <-- to run your script

```

---

### Post by ComplexNumber on 2006-04-17
1) it should be in the menu. are you sure its not there? it should be.

2) you don't *have to* create script files. what exactly are you trying to do? create scripts in any editor (eg gedit, kwrite(for kubuntu), etc).

3) have a read of [this]("http://linux.org.mt/article/terminal"). many scripts are created using a linux scripting langage such as bash. you can also use other scripting languages such as perl(not recommended until you are doing serious work with strings) or python(a nice  and easy to learn language) etc.

---

### Post by hippobottomus on 2006-04-17
Thanks to all.  Very helpful. :-D 

I found I needed to install Terminal via Add Applications - now installed. 

I'll try those commands, thanks.  

I'm trying to run any scripts (mainly for testing) so as to get the hang of it and see how it all works.

---

### Post by ds[de] on 2006-04-17
I think by default gnome opens a Terminal when you press CTRL + 5 (NumBlock), which is probably the fastest way to do it.

Regards,
ds[de]

---

### Post by ncappel1 on 2006-04-18
I like to set it so that my "windows" key between ctrl and alt opens a window. I never use it for other meta functions. It's nice and quick and easy to remember, I chose the windows key because I thought it a little bit tounge and cheek.

you can set some simple meta keys in System-->preferences-->keyboard shortcuts

---

