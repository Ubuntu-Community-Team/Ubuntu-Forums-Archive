---
title: "terminal question"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by xubu_caapn on 2007-07-13
hey everyone, i have devilspie running to get a terminal in my desktop. works fine, but i wanted to use it to run programs, which i can do, but i can't type any more commands until i close the program i opened with the terminal. anyway to circumvent this?

also, is there a way to shorten binaries names? for instance rather than typing firefox i type "ff"?

---

### Post by diafanos on 2007-07-13
> **xubu_caapn said:**
> hey everyone, i have devilspie running to get a terminal in my desktop. works fine, but i wanted to use it to run programs, which i can do, but i can't type any more commands until i close the program i opened with the terminal. anyway to circumvent this?


You have to run your program in the background. To do that just type program's name and add &, e.g. in case you want to start gedit, type "gedit &"

> **xubu_caapn said:**
> 
also, is there a way to shorten binaries names? for instance rather than typing firefox i type "ff"?
Just create a link to this file. For example, in case of firefox type:
"sudo ln -s /usr/bin/firefox /usr/bin/ff"

Than if you want to start firefox, just type ff....

---

### Post by KIAaze on 2007-07-13
To keep the programs running:
```
<command> &
```

(But if you close the terminal, the programs will be killed.)

To shorten the name of binaries, you can create symbolic links to them:
example for firefox:
```
mkdir ~/bin
```
```
ln -s /usr/bin/firefox ~/bin/ff
```
Then add this line to your ~/.bashrc file:
```
export PATH=~/bin:$PATH
```

edit:
Or just create the link in the /usr/bin directory as suggested in the previous post.
You will also make it available to other users that way.

---

### Post by hyper_ch on 2007-07-13
or you could run screen and run the appz in different virtual terminals...

---

### Post by xubu_caapn on 2007-07-13
thanks for the replies. i can now open firefox by typing in ff. i even learned a new trick. i accidentally typed in ff ff and it brought up "ff.com". very convenient, i didn't know i could do that.

this isn't working with thunderbird, however. i try "sudo ln -s /usr/bin/mozilla-thunderbird /usr/bin/brd". it creates the symlink but i can't open up thunderbird. here's the error:

```
run-mozilla.sh: Cannot execute /usr/lib/mozilla-thunderbird/brd-bin.

```

---

### Post by diafanos on 2007-07-13
You can intercept this with the following way:

Delete the symbolic link you created before, in /usr/bin

Create a file and write in it :
> #!/bin/bash
/usr/bin/mozilla-thunderbird &

Save it with any name you prefer (e.g. brd), in /usr/bin

Then in terminal write
> 
cd /usr/bin
sudo chmod +x brd (or whatever name you saved it)

Than it's ok. just type in a terminal 
> brd

---

### Post by xubu_caapn on 2007-07-13
thank you, worked perfect.
do you know why this was necessary?

---

### Post by Nythain on 2007-07-13
even better than creating symlinks... create aliases in your ~/.bashrc ... such as
alias www='firefox'
or
alias ff='firefox'

aliases, in my opinion are much easier than mastering the art of symlinks, and very very usefull/efficient

---

### Post by avik on 2007-07-14
> **xubu_caapn said:**
> thank you, worked perfect.
do you know why this was necessary?

I'm guessing the binary uses the name of used to execute it, and when you executed it with the name brd, it's assumptions about the names of certain files resulted in an error.

Once again, I would say aliases are better and cleaner for this purpose.

---

### Post by diafanos on 2007-07-14
> **Nythain said:**
> even better than creating symlinks... create aliases in your ~/.bashrc ... such as
alias www='firefox'
or
alias ff='firefox'

aliases, in my opinion are much easier than mastering the art of symlinks, and very very usefull/efficient

Yeah...Right. I didn't think of this solution...
It's much better, indeed

---

### Post by xubu_caapn on 2007-07-15
i've set all my commonly used programs up with symlinks, but i'll probably delete them and try aliases. why do you say they're better?

---

