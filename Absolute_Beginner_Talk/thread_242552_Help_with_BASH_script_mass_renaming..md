---
title: "Help with BASH script: mass renaming."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by toykilla on 2006-08-23
So I am trying to learn some bash scripting and the best way I learn is "reverse engineering". Let's say I have alot of images I want to rename. They are well organized into directories:

/main/sub1
/main/sub2
etc...

I would like to know how to create a BASH script to rename all image files inside main and the subfolders. The final file name should be either:

main-sub1-001.jpg
main-sub1-002.jpg
main-sub1-003.jpg
etc...

or

sub1-001.jpg
sub1-002.jpg
sub1-003.jpg
etc...

If you can provide a script, any explanation as to what each command is doing would be great. Any help would be appreciated!

---

### Post by NewDisciple on 2006-08-24
If you look in your synaptic package manager there is an application called mrename which handles mass renaming.

---

### Post by toykilla on 2006-08-24
cool :)   i would still like to know how to do it in a script

---

### Post by tribaal on 2006-08-24
Well script-wise you should start by taking a quick lecture at the [advanced bash scripting guide]("http://www.tldp.org/LDP/abs/html/"), it's like... the ultimate ressource for bash scripting (in my very humble opinion).

Then what you wish to do is to loop over files in a directory. You can use a FOR construct here:
```

for file in *
do

# This is where you rename each $file
mv $file $file'-2'

done 
```

This is just a sketch, but I guess you get the idea.

Hope this helps...

- trib'

---

