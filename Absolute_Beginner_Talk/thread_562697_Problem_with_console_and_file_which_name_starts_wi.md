---
title: "Problem with console and file which name starts with &quot;-&quot;"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Mr.nano on 2007-09-29
hay, I have this a little bit weird problem:

I want to move some files form one folder to another but the files name starts with "-" (minus symbol) so when I enter the command it gives me with a reason invalid option because it is thinking   that am going to pass a option to the command and not a file name.
So what's the deal? How should I fix that?

(I could copy the file name because with copy and paste in the console but image if had only command line without graphics like gnome)

---

### Post by bodhi.zazen on 2007-09-29
LOL

- is a funny thing as it typically signifies options.

Let us say the directory is named -foo

cd \ -foo

The syntax is backlash (the one above the enter key) <space> -foo

works for directories and files

---

### Post by Mr.nano on 2007-09-29
i still cant do that, the name starts with "-~sometext" so when when i type:
mv \-~sometxt
it gives me invalid option -- ~
once again what should i do?

---

### Post by dcstar on 2007-09-29
> **Mr.nano said:**
> i still cant do that, the name starts with "-~sometext" so when when i type:
mv \-~sometxt
it gives me invalid option -- ~
once again what should i do?

Try putting the filename in quotes as you did in the message.

---

### Post by Mr.nano on 2007-09-29
Nope it doesn't work.
I also tried 
mv \-\~sometext 
but the result was the same

Any other suggestions?
This happened to be quite irritating!!!

---

### Post by Bothered on 2007-09-29
You could use nautilus to move/rename the file, but that's not a solution if you want to deal with files like this in the command line.

---

### Post by Maxtorm on 2007-09-29
Use a wildcard:
```
mv *sometext new_file_name
```

---

### Post by bodhi.zazen on 2007-09-29
> **Mr.nano said:**
> i still cant do that, the name starts with "-~sometext" so when when i type:
[color=red]mv \-~sometxt[/color]
it gives me invalid option -- ~
once again what should i do?

Looks like you forgot the space between the \ and the -

> bodhi@VirtualUbuntu:~$ touch \ -~sometext
bodhi@VirtualUbuntu:~$ ls | grep sometext
 -~sometext
bodhi@VirtualUbuntu:~$ mv \ -~sometext \ -~someothertext
bodhi@VirtualUbuntu:~$ ls | grep some
 -~someothertext
bodhi@VirtualUbuntu:~$

Note the space between "\" and "-~sometext" and in your first example you used a | and not a \

Maxtorm's solution works as well, but not if you wish to preserve the -

If you wish to preserve the - you need

mv *sometxt \ -newtext

Again, notice the \ followed by a space and then the -newtext

---

### Post by Mr.nano on 2007-09-29
strangely or not, but when i typed:
mv *sometext* the answer again was:
mv: invalid option -- ~
haha that's really amazing!

---

### Post by asmoore82 on 2007-09-29
you need to specify what directory the file is in; which would be a single dot ``.''
for the current working direcotry. AND you **might** need to use single quotes to keep
the shell from interpreting ``~'' as the HOME directory; **better safe than sorry**.

```
~$ mv './-~strange_filename!!with spaces' normal_filename
```

---

### Post by bodhi.zazen on 2007-09-29
/bodhi waits for Mr.nano to try his advice

> bodhi@VirtualUbuntu:~$ touch \ ~sometext
bodhi@VirtualUbuntu:~$ ls | grep text
 [color=blue]~sometext[/color]
bodhi@VirtualUbuntu:~$ [color=blue]mv \ *sometext newtext[/color]
bodhi@VirtualUbuntu:~$ ls | grep text 
[color=green]newtext[/color]
bodhi@VirtualUbuntu:~$  

No quotes required

---

### Post by Mr.nano on 2007-09-29
OK! I did it.
I chose the way that asmoore82 showed, but without the single quotes. I just typed:
mv ./*sometext* foldernameinsamedir/  (and it worked)

But after that another question arised, I tried it once just to enjoy it works - move it back to the old destination, like this:
mv ./*sometext* cd ..
the aswer was:
mv: cannot stat `cd': No such file or directory

-but however it did the job it moved the file to the upper directory from where it came from, ain't that a little bit strange?

And,
bodhi could you tell me what the above is going to do I didn't managed to do it?
Some other ways to do that?

10X Guyz, you've helped me a lot! I do appreciate that!

---

### Post by bodhi.zazen on 2007-09-29
> **Mr.nano said:**
> OK! I did it.
I chose the way that asmoore82 showed, but without the single quotes. I just typed:
mv ./*sometext* foldernameinsamedir/  (and it worked)

But after that another question arised, I tried it once just to enjoy it works - move it back to the old destination, like this:
mv ./*sometext* cd ..
the aswer was:
mv: cannot stat `cd': No such file or directory

-but however it did the job it moved the file to the upper directory from where it came from, ain't that a little bit strange?

And,
bodhi could you tell me what the above is going to do I didn't managed to do it?
Some other ways to do that?

The problem is with the "cd"

should be mv ./*sometext* ..

. = current directory
.. = parent directory

format of mv

mv {options} <file 1> <file 2> <file ...> [destination]

so, in your command you got an error when you tried to move the file "'cd" to ..
The command moved ./*something* to ..

> 10X Guyz, you've helped me a lot! I do appreciate that!

As a general tip, you can get this kind of information from the man pages. I know they are written in geek, but if you start to use them you will soon find them invaluable.

They are even abailable on-lin:
[man mv](http://unixhelp.ed.ac.uk/CGI/man-cgi?mv)

The rest is just understanding how bash interpret wild cards, white space, and special symbols. Often there is more then one way to skin a cat and as you gain experience you will skin them too. Usually one way is no better then any other. There is nothing wrong with wild cards, but i was trying to show you more about more options and some of the how and why.

Another choice you have is tab completion. This works for files, directories, and programs.

Hit this sequence of keys for example :

c d / h o <tab> <tab> (without the spaces) You should see :

cd /home/<user_name> where <user_name> is your log-in name or a list of users in /home if there is more then one.

---

### Post by Mr.nano on 2007-09-30
Ok 10X again!

...and something more to ask:
when I use the backslash to avoid blank spaces in files and folders' names like this:
cd Docs\ and\ Setts (to movet to Docs and Setts folder for example)

why the following doesn't work for my file:
mv \-\~myfile myfilewithoutthe-

---

### Post by bodhi.zazen on 2007-09-30
Well Bash uses "special characters" and ~ is one of them.

~ = /home/username

But you can also user tab completion with ~ and usernames :twisted:

So you can type ~bo<tab> and (on my box) you will get ~bodhi

If will also note ls ~ == ls ~bodhi

I do not know why you can not escape the ~ with a \~

[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x206.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x206.html)

[http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/special-chars.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/special-chars.html)

---

### Post by Mr.nano on 2007-10-04
10X 4 the links, quite useful for me!

---

