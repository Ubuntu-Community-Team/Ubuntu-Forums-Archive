---
title: "Easy Script Questions"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-09
Hello All !!!

I am trying to do some Scripting, since I have realized that it is so powerfull.

First I would like to ask you this:

Line 1: echo "Please give me your name:"
Line 2:
Line 3: read namegiven
Line 4:
Line 5: echo""
Line 6: echo"The name you gave is: $namegiven"
Line 7: echo""

_Question1_:
What do I have to change to the above "Line 6" to actually print (give me) the $namegiven? (cause it does not give me the name...)

_Question2_:
How can I combine "Lines 5-7" in one SINGLE line?
(I know in the "C" programming language, you would do a printf("\nThe ...blah...blah\n") command). You actually use the "\n"...
How do I do this in the Script language?

_Question3_:
I want to be able to change the name given (e.g. TONY) to ALL non-caps (e.g. tony). An input of "TONY" should output "tony".

_Question4_:
I also want to check if the name "tony" exists in my home directory (e.g. if there actually exists a "/home/tony" directory).
How can I do that?

I know that ALL the above are TOO easy for you...
For me, it is just too difficult...

Thanks.

P.S.> Where can I find in the Internet, Script Commands (with explanation of what they do, when used)?

---

### Post by soce_32 on 2006-03-09
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

---

### Post by bluevoodoo1 on 2006-03-09
[QUOTE=dvarsam]
P.S.> Where can I find in the Internet, Script Commands (with explanation of what they do, when used)?[/QUOTE]

Well, I'm not too familiar with scripts so I can't help with your question. But for your reading... have you seen this site? [http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

---

### Post by dvarsam on 2006-03-09
Hello All !!!

I managed to find a solution to Questions 1 & 2:

You have to remove lines 5 & 7, and replace line 6 with the following:

echo -e \\n"The name you gave is:" $namegiven \\n

Basically the "$namegiven" has to be outside the quotes.
The "-e" option, enables interpretation  of  the following backslash-escaped characters.
The first "\" option tells Shell that escaped (special) characters are going to be used.
The following "\n" tells Shell to move to the next line.

Any ideas on how to solve Questions 3 & 4?

Thanks in advance.

---

### Post by dvarsam on 2006-03-09
_Feedback from Author_:

Regarding the "Question 4", I have managed the following:

Line 01: echo "Please give me your name:"
Line 02:
Line 03: read namegiven
Line 04:
Line 05: echo -e \\n"The name you gave is:" $namegiven \\n
Line 06:
Line 07: echo -e "Now we are going to check if a directory named" \"$namegiven\" exists:\\n
Line 08:
Line 09: test="/home/$namegiven/Desktop"
Line 10:
Line 11: echo $test           ( <- I put this just to see my point)
Line 12: pwd                     ( <- I put this just to see my point)
Line 13:
Line 14: if [ $test=pwd ]; then
Line 15: echo Folder $namegiven exists.
Line 16: else echo Folder $namegiven does not exist.
Line 17: fi

But I have the following problem:

_Output 1_:
root@ubuntu:/home/dimitris/Desktop# sh a.sh

Please gime me your name:
dimitris

The name you gave is: dimitris

Now we are going to check if a directory named "dimitris" exists:

/home/dimitris/Desktop     (<- This is what we want)
/home/dimitris/Desktop     (<- This is what we want)

Folder dimitris exists.         (<- Result OK)

_Output 2_:
root@ubuntu:/home/dimitris/Desktop# sh a.sh

Please gime me your name:
tony

The name you gave is: tony

Now we are going to check if a directory named "tony" exists:

/home/tony/Desktop           (<- This is what we typed)
/home/dimitris/Desktop       (<- This is different directory)

Folder tony exists.               (<- This is WRONG !!! - It does NOT exist!!!)


Please help me, what am I doing wrong here?

Thanks!

---

### Post by dvarsam on 2006-03-10
I just figured what to add as my Signature...

_This is it guys_:

#!/bin/bash

if [ Ubuntu_Forum=Exist ] ; then

	echo "Why don't I get any response from you guys?"

else

	echo "Ubuntu Forum does NOT Exist!"

fi

Thanks.

P.S.>  If you try to run it, it will EXIST!
          In reality though, where are the "Shell" Experts?
          I mean, YOU guys?

---

### Post by Jimmy_r on 2006-03-10
I dont script, but if it was programming, i would say

Line 14: if [ $test=pwd ]; then

Should be

Line 14: if [ $test==pwd ]; then

---

### Post by Jimmy_r on 2006-03-10
if [ 1==2 ]; then
echo Right;
fi

Right

if [ 1=2 ]; then
echo Right;
fi

Right

Right... Me will just stick to python and C, thankyouverymuch :p

---

### Post by dvarsam on 2006-03-10
Thanks for your reply !!!

I have tried it & it does NOT work!

No matter which "input" I give, I ALWAYS get an output "Folder exists".

So, the comparison does not work...

At the same time (I think), that the "==" you are suggesting does NOT work in the "Bash Shell" language, but ONLY in the "C" programming language... 

If in some way, I could isolate from "/home/dimitris/Desktop" just the "dimitris" part, maybe the comparison would work...

& comparing that with the user "input" could work.

But I do NOT know how to do this...

Instead, by doing some yahooing I have ONLY managed to find comparing "File names" & NOT "Folder names" or "Paths"...

Thanks.

P.S.> Basically I am trying to create a Script that installs FONTS on a per user basis.
         So, it creates a ".fonts" folder in the USER directory, as long as the USER 
         exists...
         So, I need to find if the User I give as "input" actually exists...
         If you work in a company:
         1. User 1 wants "German" typing fonts installed.
         2. User 2 wants "French" typing fonts installed.
         3. User 3 wants "Spanish" typing fonts installed.

         However, User1 does NOT want "French" or "Spanish" fonts installed, 
         because he does NOT speak those languages...
         At the same time, User2 does NOT want "German" or "Spanish" fonts 
         installed, because he does NOT speak those languages...
         Same happens to User3...
         It helps install fonts available on a per-user basis...

---

### Post by Jimmy_r on 2006-03-10
This works... :p

```
#! /usr/bin/env python

import os

namegiven=raw_input("Please give me your name: ")
print "The name you gave is:", namegiven
print "Now we are going to check if a directory named", 
print namegiven,"exists:"
test="/home/"+namegiven+"/Desktop"
print test
print os.getcwd()
if test == os.getcwd():
    print "Folder",namegiven,"exists."
else:
    print "Folder",namegiven,"does not exist."
```

os.getcwd() gives the current working directory, as pwd does. It may not be what you want?

This may be better:

```
#! /usr/bin/env python

import os

username=raw_input("Please give me your username: ")
path="/home/"+username+"/Desktop"
if os.path.exists(path):
    print "Yes"
else:
    print "No"
```

Just had to... Me like python :)

---

### Post by trorion on 2006-03-10
[QUOTE=dvarsam]
P.S.> Basically I am trying to create a Script that installs FONTS on a per user basis.
         So, it creates a ".fonts" folder in the USER directory, as long as the USER 
         exists...
         So, I need to find if the User I give as "input" actually exists...
         If you work in a company:
         1. User 1 wants "German" typing fonts installed.
         2. User 2 wants "French" typing fonts installed.
         3. User 3 wants "Spanish" typing fonts installed.

         However, User1 does NOT want "French" or "Spanish" fonts installed, 
         because he does NOT speak those languages...
         At the same time, User2 does NOT want "German" or "Spanish" fonts 
         installed, because he does NOT speak those languages...
         Same happens to User3...
         It helps install fonts available on a per-user basis...[/QUOTE]
Would someone explain how he can do this by default when the user is created?  I've been trying to get to this type of thing myself (got bogged down when I corrupted my hda1 NTFS and I had to go get my 'manuals' for chkdsk).

---

### Post by dvarsam on 2006-03-10
Dear "Jimmy R",

Thank you for the code you suggested, but it does NOT work...

root@ubuntu:/home/dimitris/Desktop# sh python.sh

_Output_:
python.sh: line 4: import: command not found
python.sh: line 6: syntax error near unexpected token `('
python.sh: line 6: `namegiven=raw_input("Please give me your name: ")'

Then tried your 2nd suggestion:

root@ubuntu:/home/dimitris/Desktop# sh python2.sh

_Output_:
python2: line 4: import: command not found
python2: line 6: syntax error near unexpected token `('
python2: line 6: `username=raw_input("Please give me your username: ")'

_Question 1_:
Am I missing any libraries (to run the above)?

I have only installed "build-essentials" - nothing else...

_Question 2_:
At the same time, my program is a "Bash Shell" & your suggestion is "Python".

Can I merge your "Python" script into the "Bash Shell" script in ONE file & start like this:

#!/bin/bash           (<- For Bash Shell)

#! /usr/bin/env python         (<- For Python Shell)

... blah ..... blah...
... blah ..... blah...
... blah ..... blah...

Would this work?

P.S. I looked for something like "os.path.exists(path)" for Shell Script, but did NOT find anything. I visited the following site for this:

[http://www.linuxcommand.org/man_pages/](http://www.linuxcommand.org/man_pages/)

---

### Post by markd on 2006-03-10
You want the -d test to check for a directory.  Something like:

```
if [ -d /home/$namegiven/Desktop]; then
```

---

### Post by dvarsam on 2006-03-10
I have managed to make it work.
When finished, I will post this.

However, I am still struggling with Question 3...

How can I change a "word" typed in ALL CAPS, to ALL SMALL CAPS?

Come on, that is easy...

There must be an option like, "convert" or "tosmallcaps" or whatever...

Please help...

Thanks.

---

### Post by dvarsam on 2006-03-10
I have found the following command:

echo "$checkname" | tr [A-Z] [a-z]

But it only converts Uppercase to Lowercase TEMPORARILY...

So if I do a:

#!/bin/bash

echo "Please gime me your name:"
# somebody types the name in ALL capital letters...

read checkname

echo "$checkname" | tr [A-Z] [a-z]
# This prints the name onscreen with small caps - only temporarily...
# It does NOT convert the ALL caps to small caps.

I have searched on "tr --help"

But I can not seem to make it work...

I have done some yahooing too, only to find more confusing stuff:

1. tr [a-z] $checkname           - does not work
2. tr 'a-z' $checkname            - does not work
3. tr [A-Z] [a-z] $ckeckname   - does not work

Please help...

Can somebody more experienced read the "tr --help" & tell me how should apply it?

Many Thanks.

---

### Post by Wolki on 2006-03-10
Try checkname=`echo "$checkname" | tr [A-Z] [a-z]`

---

### Post by Jimmy_r on 2006-03-11
Trorion, if you want to control what a new user gets in his home directory by default, you may want to investigate /etc/skel.
LFS has a lot of useful information for such tings: [http://www.linuxfromscratch.org/blfs/view/stable/postlfs/skel.html](http://www.linuxfromscratch.org/blfs/view/stable/postlfs/skel.html)

And now just for my personal amusement, lets compare this to how your script will be, dvarsam. Its funny to compare programming languages:

```
#! /usr/bin/env python

import os, sys, shutil

i=0
t=0
while i!=1:
    username=raw_input("Please give me your username: ")
    path="/home/"+username
    if os.path.exists(path):
        i=1
    else:
        t=t+1
        if t>=3:
            sys.exit(0)
        print "That name is not valid. Please try again."

fontpath=path+"/.fonts"
print "Which language do you prefer?"
i=0
t=0
while i!=1:
    language=raw_input("1 for German, 2 for French or 3 for Spanish: ")
    if language == "1":
        i=1
        shutil.copytree("germanfontpath", fontpath)

    elif language == "2":
        i=1
        shutil.copytree("frenchfontpath", fontpath)

    elif language == "3":
        i=1
        shutil.copytree("spanishfontpath", fontpath)

    else:
        t=t+1
        if t>=3:
            sys.exit(0)
        print "Invalid choice. Please try again."

```
replace "germanfontpath", "frenchfontpath" and "spanishfontpath" with the actual paths
save as something.py 
chmod +x something.py
./something.py

---

### Post by dvarsam on 2006-03-12
Dear "Wolki",

                     it worked, thanks!

 Dear "Jimmy R",

                          I am still under development. It works nice, but I am getting the wrong output (I have designed a bad "if" statement).
However, I want to do it in an automated way, so I get minimum input from the user who will run this.
When done, I will give it to the Ubuntu community.
Thanks.

---

