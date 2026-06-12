---
title: "The Unnecessarily Feature-laden Bash Script Game"
date: 2008-04-27
forum: Cafe Games
---

### Post by |{urse on 2008-04-27
The aim of this thread is to post a bash script that works but has too many features to warrant it's existence.

Sample:
```
#!/bin/bash
#runs frostwire
frostwire
clear
xmessage -center "hello, `whoami`" -buttons "Hey There":0]
if [ "`whoami`" == "kurse" ]
#change "kurse" to your username and change all subsequent kurses as well 
then
echo "Welcome kurse.. let's sync your new stuff"
#edit this to say whatever or just delete it
cd /home/kurse/Shared
ls > /home/kurse/Desktop/~listmusic
xmessage -center -file /home/kurse/Desktop/~listmusic
#a nice little popup tells you what is about to be copied 
cp /home/kurse/Shared/* /home/kurse/Desktop/Frostwire 
#assuming you have created a folder called Frostwire on your desktop
xmessage -center All Files Synchronized
sudo rm -rf /home/kurse/Shared/*
#all files in Shared are removed and no longer shared with the world
#I wonder.. does this make downloading copyrighted material less illegal?
clear
echo -e '\E[33;44m'"cleaning up..."; tput sgr0
banner -w25 "OK!"
sudo rm -rf /home/kurse/Desktop/~listmusic
touch /home/kurse/Desktop/~listmusic
cd /home/kurse/Shared/
ls > /home/kurse/Desktop/~listmusic
echo "All Done Here!"
read -p "press enter to EXIT" var
#just makes you press enter unecessarily
exit
else
echo "You are not kurse, perhaps you copied this and didn't change things properly to work with your system"; 
exit
fi . 
```

sadly all that was needed in this case was to copy files from one dir to another  !

please post your overly-featured bash scripts (one at a time pls) and also feel free to participate by guessing exactly how many of the lines in the script were valid but totally unecessary!

Edit: Don't run anyones unnecessary scripts unless you know what they are overdoing.

---

### Post by |{urse on 2008-05-03
lol noone? i know a bunch of you linux nerds have at least one shamefully overbloated bash script sitting on your hard drives somewheres! :lolflag:

---

### Post by Hickory420 on 2012-01-21
[FONT="Courier New"]I'm starting to learn bash and I also don't like doing things the long way. But, I do like doing things properly. I will work hard to make thing easy.

So with that said... I have actually learned quite a bit modifying your original script. I even added error control!! 

```

#!/bin/bash
clear
if ! [ "`whoami`" == "ubuntu" ]; then
	echo "You are not who you think you are... see a shrink."
	exit
fi
CRAP1=/home/ubuntu/Desktop/crap1
CRAP2=/home/ubuntu/Desktop/crap2
echo "Welcome ubuntu.. let's sync your new stuff"
if ! [ "$(ls $CRAP1)" ]; then
	echo "Nothing to sync right now!"
	exit
fi
cp $CRAP1/* $CRAP2/ || echo "failed to copy... i've just protected your.. stuff." exit
echo -e '\E[33;44m'"House keeping..."; tput sgr0
sudo rm -rf $CRAP1/*
ls > $CRAP2/ListOfCrap
touch $CRAP2/ListOfCrap
echo "All Done Here!"
exit

```

Got anymore bloated crap I can attempt to clean up? :P[/FONT]

---

### Post by Metallion on 2012-01-22
I don't really have any scripts like that on my comp. Only tiny single-feature ones. The closest I've got would probably be this script that takes a Ubuntu lucid server CD and turns it into a Wakame-VDC demo installer. (ie a single server IaaS cloud)

[https://github.com/axsh/wakame-vdc/blob/master/tests/cd_builder/build_cd.sh](https://github.com/axsh/wakame-vdc/blob/master/tests/cd_builder/build_cd.sh)

I've written the bulk of it but my colleagues have been improving it lately.

As for the OP script, I'd suggest keeping the username in a variable. Like this:

```

#!/bin/bash

USERNAME=ubuntu

clear
if ! [ "`whoami`" == $USERNAME ]; then
	echo "You are not who you think you are... see a shrink."
	exit
fi
CRAP1=/home/$USERNAME/Desktop/crap1
CRAP2=/home/$USERNAME/Desktop/crap2
echo "Welcome $USERNAME.. let's sync your new stuff"
if ! [ "$(ls $CRAP1)" ]; then
	echo "Nothing to sync right now!"
	exit
fi
cp $CRAP1/* $CRAP2/ || echo "failed to copy... i've just protected your.. stuff." exit
echo -e '\E[33;44m'"House keeping..."; tput sgr0
sudo rm -rf $CRAP1/*
ls > $CRAP2/ListOfCrap
touch $CRAP2/ListOfCrap
echo "All Done Here!"
exit

```

Makes it easier to reuse it for other users.

---

### Post by |{urse on 2012-05-15
"unnecessary (maybe even funny) features" you can add to scripts pls? :)

---

### Post by Metallion on 2012-05-15
If you give me your credit card details, I can add a feature that pays me a 1000 bucks a minute. ^_^

---

### Post by |{urse on 2012-05-16
[IMG]https://en.bitcoin.it/wiki/Casascius_Bitcoin_POS_system[/IMG] [https://en.bitcoin.it/wiki/Casascius_Bitcoin_POS_system](https://en.bitcoin.it/wiki/Casascius_Bitcoin_POS_system)  :lolflag: 
Currently writing a script that does what that does with a usb card reader, incidentally.

---

