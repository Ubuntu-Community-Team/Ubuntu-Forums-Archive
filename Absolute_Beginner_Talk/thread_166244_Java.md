---
title: "Java"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by RobyX on 2006-04-26
Im going insane trying to install this, im looking for a simple and straight forward guide. The on in the wiki isint working.

All I want to do is run Azerus and Frostwire.. for the past several hours been trying to get this, getting to the point where im going to pay someone to do it..:(

---

### Post by joshrobinson on 2006-04-26
download the latest jre.bin file from the java website
[https://sdlc6c.sun.com/ECom/EComActionServlet;jsessionid=464932B3368895B3EB56B251EE837FBD]("https://sdlc6c.sun.com/ECom/EComActionServlet;jsessionid=464932B3368895B3EB56B251EE837FBD")

next put the bin file where you want it to install.. such as / or /usr wherever

next open a terminal and browse where you have the .bin file

sudo chmod +x binfilename.bin    (put the name of the file instead)
next
sudo ./binfilename.bin  (again put the name of the file instead)

hit q to get past the terms of use
type yes to continue installing

now do
java -version  to see if it comes up with the right version number
if nothing comes up, or the wrong version number go into /usr/bin
you will see a file called java. rename it to say java2 (if you dont see it skip the rename file step)

next make a symbolic link to the java file where you installed it
say you put it in /usr/java
the file you want should be in /usr/java/jre1.5.0_06/bin

so do

ln -s /usr/java/jre1.5.0_06/bin/java
while being in  /usr/bin in your terminal

last do java -version again to make sure its 1.5.0

---

### Post by RobyX on 2006-04-26
[QUOTE=joshrobinson]
next open a terminal and browse where you have the .bin file
[/QUOTE]

:confused:

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]:confused:[/QUOTE]

applications > accessories > terminal

type:
sudo nautilus

a file browser should open up with root privealges
go to /usr
create a new folder called java
copy the .bin file you downloaded into the /usr/java folder

close the file browser window
now in terminal type
cd /usr/java

now type chmod +x binefilename.bin
then
./binefilename.bin
hit q at the term of use information
then type yes

---

### Post by RobyX on 2006-04-26
EDIT: Nevermind works im dumb. Thanks for the help..

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]```

roby@Roby:~$ cd /usr/java
roby@Roby:/usr/java$  chmod +x jre.bin
roby@Roby:/usr/java$ /jre.bin
bash: /jre.bin: No such file or directory
roby@Roby:/usr/java$

```

I renamed the file to jre.bin if you're wondering.
I did it exactly step by step it should have worked[/QUOTE]

do
sudo chmod +x jre.bin  
then sudo **./jre.bin**    there is a period before the / i know its kinda hard to see on here

---

### Post by RobyX on 2006-04-26
java version "1.4.2-02"

Can I just use this version? I can't rename files in usr/bin anyway.

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]java version "1.4.2-02"

Can I just use this version? I can't rename files in usr/bin anyway.[/QUOTE]

1.4.2 gave me problems with azureus.. i had to use 1.5.0

in your terminal:

sudo nautilus

(sudo gives you root abilities.. so you can edit any file)
go to usr/bin and rename the java file java2 or java_backup

when youve done the rename, close the file browser

navigate to /usr/bin in the terminal by typing:
cd /usr/bin

it should say /usr/bin after your terminal name
then execute

sudo ln -s /usr/java/jre1.5.0_06/bin/java

do another java -version

---

### Post by RobyX on 2006-04-26
[QUOTE=joshrobinson]1.4.2 gave me problems with azureus.. i had to use 1.5.0

in your terminal:

sudo nautilus

(sudo gives you root abilities.. so you can edit any file)
go to usr/bin and rename the java file java2 or java_backup

when youve done the rename, close the file browser

navigate to /usr/bin in the terminal by typing:
cd /usr/bin

it should say /usr/bin after your terminal name
then execute

sudo ln -s /usr/java/jre1.5.0_06/bin/java

do another java -version[/QUOTE]

```

roby@Roby:~$ sudo nautilus

--- Hash table keys for warning below:
--> file:///usr
--> file:///

(nautilus:10868): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///usr
--> file:///

(nautilus:10868): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time (keys above)
roby@Roby:~$


```

I renamed it to Java2, then right when I close it I get all these lines of errors.

---

### Post by joshrobinson on 2006-04-26
ok in terminal

change directory to /usr/bin

cd /usr/bin
type:

ls

and it will show you all the files in that directory, look for java or java2 to see if the rename worked

if its still named java do the following

sudo mv java java2

---

### Post by RobyX on 2006-04-26
OK I did that and it's not named Java.
Am I doomed?

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]OK I did that and it's not named Java.
Am I doomed?[/QUOTE]

linux is case sensitive, so make sure you use lowercase

try this now

sudo ln -s /usr/java/jre1.5.0_06/bin/java

while you are in the /usr/bin directory

---

### Post by RobyX on 2006-04-26
The file renamed:
[http://img159.imageshack.us/img159/7274/screenshot1tp.png](http://img159.imageshack.us/img159/7274/screenshot1tp.png)

When I put those commands in:
[http://img137.imageshack.us/img137/9417/screenshot19ya.png](http://img137.imageshack.us/img137/9417/screenshot19ya.png)

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]The file renamed:
[http://img159.imageshack.us/img159/7274/screenshot1tp.png](http://img159.imageshack.us/img159/7274/screenshot1tp.png)

When I put those commands in:
[http://img137.imageshack.us/img137/9417/screenshot19ya.png](http://img137.imageshack.us/img137/9417/screenshot19ya.png)[/QUOTE]

sudo rm java

while in the /usr/bin directory

then try the
sudo ln -s /usr/java/jre1.5.0_06/bin/java

actually use a file browser to go into /usr/java  is the folder in there named the same as above?

---

### Post by RobyX on 2006-04-26
[QUOTE=joshrobinson]sudo rm java

while in the /usr/bin directory

then try the
sudo ln -s /usr/java/jre1.5.0_06/bin/java

actually use a file browser to go into /usr/java  is the folder in there named the same as above?[/QUOTE]

```
roby@Roby:~$ cd /usr/bin
roby@Roby:/usr/bin$ sudo rm java
roby@Roby:/usr/bin$ sudo ln -s /usr/java/jre1.5.0_06/bin/java
roby@Roby:/usr/bin$

```

Im not sure if those commands did anything at all.

And that java above java2 is broken and it keeps coming back even if I delete it.

Dude I really hope Linux doesent get much harder then this..

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]```
roby@Roby:~$ cd /usr/bin
roby@Roby:/usr/bin$ sudo rm java
roby@Roby:/usr/bin$ sudo ln -s /usr/java/jre1.5.0_06/bin/java
roby@Roby:/usr/bin$

```

Im not sure if those commands did anything at all.

And that java above java2 is broken and it keeps coming back even if I delete it.

Dude I really hope Linux doesent get much harder then this..[/QUOTE]

you get used to it

go into /usr/java with a file browser and tell me what the name of the folder is in there
is it jre1.5.0_06?

---

### Post by RobyX on 2006-04-26
It's j2re1.4.2_11

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]It's j2re1.4.2_11[/QUOTE]

ahh crap thats our problem

sudo nautilus

go into /usr/java  and delete that folder and the old .bin file in there

[http://192.18.108.136/ECom/EComTicketServlet/BEGIN0D49F66D86BF9F27FFD75EF9B1F2A98F/-2147483648/1450318671/1/682154/682058/1450318671/2ts+/westCoastFSEND/jre-1.5.0_06-oth-JPR/jre-1.5.0_06-oth-JPR:20/jre-1_5_0_06-linux-i586.bin]("http://192.18.108.136/ECom/EComTicketServlet/BEGIN0D49F66D86BF9F27FFD75EF9B1F2A98F/-2147483648/1450318671/1/682154/682058/1450318671/2ts+/westCoastFSEND/jre-1.5.0_06-oth-JPR/jre-1.5.0_06-oth-JPR:20/jre-1_5_0_06-linux-i586.bin")

grab this .bin file.. put it in /usr/java

sudo chmod +x java.bin
sudo ./java.bin

then a java -version again.. that should do it

so now it should be /usr/java/jre1.5.0_06/

---

### Post by RobyX on 2006-04-26
Did I do it correctly?

[http://img137.imageshack.us/my.php?image=screenshot7ka.png](http://img137.imageshack.us/my.php?image=screenshot7ka.png)

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]Did I do it correctly?

[http://img137.imageshack.us/my.php?image=screenshot7ka.png](http://img137.imageshack.us/my.php?image=screenshot7ka.png)[/QUOTE]

yes you did :D :mrgreen: 

as long as java -version comes back with 1.5.0_06 your all good to go

---

### Post by RobyX on 2006-04-26
Sweet finnaly, JAVA!
I defitnly have to save all this info. Thanks alot man

---

### Post by joshrobinson on 2006-04-26
[QUOTE=RobyX]Sweet finnaly, JAVA!
I defitnly have to save all this info. Thanks alot man[/QUOTE]

no problem 

have fun with ubuntu :D

---

