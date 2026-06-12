---
title: "Simple Command Line Query"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Carandol on 2007-06-11
I'm messing about with a minimalist system at the moment, and toying with the idea of running commands from the terminal. This works fine for things like "firefox &", but my word processor TextMaker, requires the command "/usr/local/office/textmaker" I'd like to make a short command such as "tm" to run this program. I know I could do it with a batch file in DOS, but I don't know what the equivalent is in linux!

---

### Post by LaRoza on 2007-06-11
a bash script, it is like batch, but to me, bash scripts are more powerfull.

I do not have much experience with bash scripting, but I'm sure you'll find something now that you know what to look for,

try searching:

"shell scripting"
"bash scripts"

---

### Post by trak87 on 2007-06-11
> **Carandol said:**
> I'm messing about with a minimalist system at the moment, and toying with the idea of running commands from the terminal. This works fine for things like "firefox &", but my word processor TextMaker, requires the command "/usr/local/office/textmaker" I'd like to make a short command such as "tm" to run this program. I know I could do it with a batch file in DOS, but I don't know what the equivalent is in linux!

Create a 'bin' directory (a place to run **bin**aries) off your home directory, then go into that directory:

```
cd 
mkdir bin
cd bin
```

Then, using your favorite editor, open a file called 'tm' and enter the following:

```
#!/bin/sh
/usr/local/office/textmaker
exit 0
```

Save and exit. Now give that file executable permissions:

```
chmod +x tm
```

You will have to exit out of your terminal and enter it again (log out and log back in) for the shell to recognize the bin directory as an executable directory. (Just for reference, look in ~/.profile and you'll see that it already specifies the user's bin directory in the path).

Then give the 'tm' command a test.

---

### Post by the_tazinator on 2007-06-11
Create a link in your /usr/local/bin directory

```
cd /usr/local/bin
ln -s tm /usr/local/office/textmaker
```

or create an alias in your .bashrc. 

```
gedit ~/.bashrc
```

and add this line with the other aliases listed

```
alias tm='/usr/local/office/textmaker'
```

then reload bashrc

```
. ~/.bashrc
```

---

