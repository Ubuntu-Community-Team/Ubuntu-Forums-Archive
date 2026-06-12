---
title: "How do you use scripts?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by gergtreble on 2007-02-22
Hey.

Im backing up my DVD collection for use on my XBMC. Ive been doing this with auto gordian knot on windows. But id love to be able to use linux to do it. Ive played around with DVD::Rip and i *could* use that.

However!

I found [this script](http://straps4linux.blogspot.com/2006/11/script-dvd2xvidsh.html) yesterday, which claims to be a one click process. Which uses mplayer, which i already have and is gathering dust in my applications menu.

But what is a script?

How do I use it?

These are important questions which need to be answered if i am going to continue my ubuntu adventure!

Thanks in advance....

---

### Post by aysiu on 2007-02-22
A script is just a text file.

Open up your favorite text editor (Gedit, Kate, Mousepad, Nano) and paste in this text: ```
#!/bin/bash

#-----------------------------------------------------------------------------------
#Show the message $1 and read from input until a Y or N are pressed
#@param $1 Message to be displayed
#@return $RV
function getAnswerYN {
   export RV="";
   while [ "$RV" != "y" -a "$RV" != "Y" -a "$RV" != "n" -a "$RV" != "N" ]
   do
       #Legge una stringa da stdin (-n 1 = un solo carattere)
       read -p "$1[y/n]" RV;
   done
}
#-----------------------------------------------------------------------------------
#Show the message $1 and wait for a response; if an empty response is
#given, it returns the second parameter (default value)
#@param $1 Message
#@param $2 Default Value
#@return $RV
function getAnswer {
   export RV="";
   read -p "$1[$2]" RV;
   [ "$RV" == "" ] && RV=$2
}
#-----------------------------------------------------------------------------------
#@param $1 Variable
#@param $2 Message
#@param $3 Default Value
#@return $1 setted
function getAnswerIfNull {
eval VAR=\$$1
if [ ! "$VAR" ]; then getAnswer "$2" "$3"; eval "$1=$RV"; fi
}
``` Save the file as *utility.sh*. Right-click the file and make sure in the properities that it's marked as executable.

If you're using Gnome, you can double-click the file and should be able to **Run in Terminal**.

---

### Post by gergtreble on 2007-02-22
And I would do that with the second script on that site too?

They seem to reference each other.

Im guessing they should be saved in /bin/bash ?

That right?

---

### Post by aysiu on 2007-02-22
No. It can be saved anywhere. I put my scripts in /usr/local/bin

#!/bin/bash just tells Ubuntu what shell to use when executing the script.

Read more here:
[http://en.wikipedia.org/wiki/Bash_shell](http://en.wikipedia.org/wiki/Bash_shell)

---

