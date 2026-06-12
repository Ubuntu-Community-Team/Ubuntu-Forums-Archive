---
title: "Mouse trouble"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by rafaelxy on 2007-07-12
My usb mtek mouse is not working completely. Both main bottons work quite well, so is the rolling pad on the center, but the click of the roll pad is not working. (when you click on a link with that, it opens automaticly in a new tab)


Another question is: how do I transform a script copied to a empty file, to a executable file?

---

### Post by pbaumgar on 2007-07-12
> **rafaelxy said:**
> My usb mtek mouse is not working completely. Both main bottons work quite well, so is the rolling pad on the center, but the click of the roll pad is not working. (when you click on a link with that, it opens automaticly in a new tab)


Another question is: how do I transform a script copied to a empty file, to a executable file?

What do you want to happen when you click the wheel?

To make a file executable, on the command line type:

chmod +x <filename>

---

### Post by rafaelxy on 2007-07-13
I want to open new tab in the firefox when clicking the wheel

---

### Post by hackle577 on 2007-07-13
> **rafaelxy said:**
> I want to open new tab in the firefox when clicking the wheel

I'm pretty sure the Tab Mix Plus extension has that functionality. I'm sort of confused though, is your mouse actually malfunctioning, or is it just not doing what you want it to do in FF?

---

### Post by rafaelxy on 2007-07-13
After this command **chmod +x <filename>** what need I to do to execute the file? I wrote the name of the file on the terminal, and got nothing....

---

### Post by hackle577 on 2007-07-13
If you did it right, it should have run. Try to find out if the script did what it was supposed to do.

---

### Post by rafaelxy on 2007-07-13
My mouse works perfectly on other OS. Ive tryed Fedora and Windows, pretty nice.

I dont know if is an Ubuntu problem or FF problem, because I only used the click from the wheel in FF.

When you click a link with the wheel, it automatically opens in a new tab, and if you click with it on the new tab, it closes.

I think is that simple... =\

---

### Post by hackle577 on 2007-07-13
I think this is purely an FF problem. 

Install the [Tab Mix Plus extension]("https://addons.mozilla.org/en-US/firefox/addon/1122") and configure it to open a new tab when the mouse wheel is clicked.

---

### Post by pbaumgar on 2007-07-13
> **rafaelxy said:**
> After this command **chmod +x <filename>** what need I to do to execute the file? I wrote the name of the file on the terminal, and got nothing....

In order for the script to run when you just type the file name, the script needs to be in your path.

Type this:  echo $PATH

Where is your script located?  In your home directory?

Without changing your path, you just need to put a "dot slash" before the script to execute it.  Type:

./<script>

---

