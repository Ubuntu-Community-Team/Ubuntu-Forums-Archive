---
title: "su password?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Fornie on 2006-06-03
hello again! :)

i know this may sound so stupid but what's the default su password? i'm using dapper drake - desktop...i went to the konsole i typed su and its asking me to enter the password, i entered my user password or a blank password NO GO...how can i change it? thanks

---

### Post by catlett on 2006-06-03
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by IrishGangsta on 2006-06-03
i too am having trouble with my su password
can anyone help besides posting a bunch of links?
thank you

---

### Post by jimrz on 2006-06-03
[QUOTE=IrishGangsta]i too am having trouble with my su password
can anyone help besides posting a bunch of links?
thank you[/QUOTE]

in terminal just type sudo <command you want>  hit enter, it will ask for password, type your login password (it will not show on screen, this is a security thing, but it is there and will work) then hit enter and do you thing

---

### Post by catlett on 2006-06-03
I can't explain the subject better than the official ubuntu document on the subject. Follow the link and read the ubuntu document on  it. It is the official explanation of why you don't use su in ubuntu but instead use sudo to invoke root priveleges.

---

### Post by meng on 2006-06-03
Hmmm, 1 link != bunch of links, but apart from that:

It is true that many new users find the sudo thing counterintuitive, particularly if they did not use it with other Linux distributions. Which is precisely why someone went to the trouble to write a comprehensive, accurate and yet concise wiki on the subject. Allowing folks like catlett to help by posting the link, in the most efficient way possible. catlett isn't being rude, and it's unfair to criticise catlett's post. Would you prefer that every response took 10 minutes, and hence fewer people were helped?

---

### Post by IrishGangsta on 2006-06-03
Well i do not know which link to chose.
But my problem is that when i enter my password i use to log into ubuntu when it starts does not work for the su
i do not know why but it just says authenticate failure.

---

### Post by meng on 2006-06-03
[QUOTE=IrishGangsta]Well i do not know which link to chose.
But my problem is that when i enter my password i use to log into ubuntu when it starts does not work for the su
i do not know why but it just says authenticate failure.[/QUOTE]
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
Don't use su, use sudo.

---

### Post by Fornie on 2006-06-03
[QUOTE=jimrz]in terminal just type sudo <command you want>  hit enter, it will ask for password, type your login password (it will not show on screen, this is a security thing, but it is there and will work) then hit enter and do you thing[/QUOTE]

please enlighten my already confuse brain :mrgreen: what are the different sudo command? thanks

i tried using su and entered my login password, i had an error message:
su: Authentication failure
Sorry

---

### Post by meng on 2006-06-03
Let's say you wanted to do the following as superuser (su): 2 commands
chmod a+x abcdef.bin
mv ghijk.so /home/fred

Instead, you type
sudo chmod a+x abcdef.bin
sudo mv ghijk.so /home/fred

And type your user password when asked.

And please read the wiki too!

---

### Post by IrishGangsta on 2006-06-03
Hmmmm
i read on that one line to type sudo -i
and it allows me to type in terminal as root
Im sorry if i came off as rude to his reply with links
i was just saying i would have liked 1 link instead of a bunch of them
but thanx for everyones help

The Answer i found to type in terminal in root is

Sudo -i

---

### Post by meng on 2006-06-03
If that answer works for you, that's fine, although it's not recommended because it sort of defeats the purpose of sudo which is to "protect" you from "accidentally" screwing your system. (Yes I know that OS straitjackets are frowned upon when the OS is made by Microsoft, but it's a reasonable compromise in my opinion.)

PS catlett has some links in his *signature*, this is possibly why you were confused and thought that multiple links were posted. The telltale sign is the horizontal line in between the post and the sig.

---

### Post by Fornie on 2006-06-03
thanks guys for your helpful replies!

ubuntu is quite addictive...i need to do lots of reading to catch up! 

for a noob's point of view, this is fun / exciting / frustrating / confusing roll into one! but i LOVE it!!! 

once again, thanks!!! :cool:

---

### Post by skinnygmg on 2006-06-03
type sudo su

---

### Post by meng on 2006-06-03
[QUOTE=Fornie]thanks guys for your helpful replies!

ubuntu is quite addictive...i need to do lots of reading to catch up! 

for a noob's point of view, this is fun / exciting / frustrating / confusing roll into one! but i LOVE it!!! 

once again, thanks!!! :cool:[/QUOTE]

Pleased it worked out for you. Remember that learning Ubuntu, as with learning anything else, requires you to put in your own effort and research. I'm not being critical of anything you've posted, I'm just asking you to keep this in mind for the future. Attitude is everything. Patience is a virtue.

---

### Post by jimrz on 2006-06-04
[QUOTE=Fornie]please enlighten my already confuse brain :mrgreen: what are the different sudo command? thanks

i tried using su and entered my login password, i had an error message:
su: Authentication failure
Sorry[/QUOTE]

<comand you want> = whatever command you are wanting to run with su priviledges (ie: sudo gedit (a file in your / directory)

---

### Post by kwahamot on 2006-12-06
I had the same problem on OSX but after reading this post I just typed "sudo passwd" (sans quotes) in the terminal window and then changed my su password to something I could easily remember, that also seemed to change my root password so everything is in sync now. I did not need to know the su password to do that, it seems, since I was logged in as myself (an administrator on the system) not root, or su... when I made the change.

Praise Ubuntu!

---

### Post by bodhi.zazen on 2006-12-06
Yes that is how to set the root password.

It is not necessary as you can always switch to root with;

sudo su

or 

sudo -s

---

### Post by kwahamot on 2006-12-06
Yes. The thing is, I knew my root passwd, but I didn't know the su password...they were different. When I typed "sudo passwd" and entered a new password, it seemed to make them all the same, so now one password works with both su and root login.

Praise Ubuntu!

---

### Post by bodhi.zazen on 2006-12-06
> **kwahamot said:**
> Yes. The thing is, I knew my root passwd, but I didn't know the su password...they were different. When I typed "sudo passwd" and entered a new password, it seemed to make them all the same, so now one password works with both su and root login.

Praise Ubuntu!

The password for sudo is your login password.

The password for su = root password

Ubuntu, as far as I can determine, sets a random password for root at the time of the install. You can set the root pw with sudo passwd .

---

### Post by devnulljp on 2006-12-06
> **meng said:**
> And please read the wiki too!
maybe you need to say 
```
sudo And please read the wiki too!

```
;-)

S/He needs to (a) read the wiki and learn how to use sudo, or (b) activate the su account. 
```
sudo passwd root
```
enter a password then s/he can su 

[IMG]http://xkcd.com/comics/sandwich.png[/IMG]

---

