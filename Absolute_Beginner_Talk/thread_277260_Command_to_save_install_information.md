---
title: "Command to save install information"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-14
Is there a way to save the install information to a text file so you can go back later and see what happened  ( ie. error messages, etc)

Something like a switch you add to the command when using the command line input ?

---

### Post by encompass on 2006-10-14
Not sure what your wanting to do... But here is something you may find usefull.
you can save a list of things you have installed with apt-get in synaptic...
Follow the image below...
Never tried it but I think you can load the list too...
Cool huh?

---

### Post by kent41 on 2006-10-14
> **encompass said:**
> Not sure what your wanting to do... But here is something you may find usefull.
you can save a list of things you have installed with apt-get in synaptic...
Follow the image below...
Never tried it but I think you can load the list too...
Cool huh?

Example: 
```
sudo aptitude install alsa-oss
```

This command when executed lists may lines of code, I would like to save the list in a text file so I could go back later and analyze  what happened.

---

### Post by encompass on 2006-10-14
You can pipe that to an output... like this...
```
sudo apt-get install a_program >> file.text
```
did it do what you wanted?
there are MANY orhter ways to do it... look up Bash Scripting for your fill of it.

---

### Post by kent41 on 2006-10-14
> **encompass said:**
> You can pipe that to an output... like this...
```
sudo apt-get install a_program >> file.text
```
did it do what you wanted?
there are MANY orhter ways to do it... look up Bash Scripting for your fill of it.

Yes that is what I was looking for **IF** it not only saves the text file but also executes the commamd in a  normal way.

If yes thank you very much for the help.
If not thanks also

Kent

---

### Post by encompass on 2006-10-14
YES it does EXECUTE in a normale way... but if you want to see the out put AND save it you use the tee cammand.
> cat fancytooltips.js | tee test.test
the format is like this...
command | tee filename
the | is called pipe is outputs everything from the previous command and gives it to the next command you type... which in this case is...
tee... tee writes the output to a file and displays what ever it gets as output to the screen too.
Cool huh?!

---

