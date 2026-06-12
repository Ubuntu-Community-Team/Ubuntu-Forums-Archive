---
title: "file recognition different between root and user"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by krajni on 2007-01-05
OK so ofter much frustration reading and learning ive overcome my first hurdle in ubunto only to uncover another.....i was having major trouble accessing a ntfs partion from users other than root.....after much studying and trial and error i found that by adding gid=100,uid=1000 to fstab i could gain access to hda6 from my basic user account
YAY
now it wont recognize anything on the drive....if i access hda6 logged in as root all the mp3's are recognized as such and will play in xmms as well as all subfolders being recognized as such.....if i access it as my user account all files and folders have a footprint icon and .mp3 wont play in xmms and when u right click what should be a subfolder and open with...>>>file browser it says could not add application to application database

any clues????

hopefully ill learn sumthing else about linux outta this mess

---

### Post by annda on 2007-01-05
you might need to set the umask option in fstab - look here for instructions:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by krajni on 2007-01-05
ok well if someone can tell me what the number values after umask stand for that would be great.....cuz one person had me make it 222  (which it still is) but ive also seen examples of it being 0222, 077, 700, and 000.....so what do they mean and how do i know what i nned ot set the value at

---

### Post by annda on 2007-01-05
quick googling tells me this:

[What is UMASK? at Tech FAQ]("http://www.tech-faq.com/umask.shtml")

that means that 222 gives all your files the 555 permissions - read and execute for owner,group and others. this looks reasonable to me, since ntfs is read-only for linux.

i must admit i don't know what the initial 0 in 0222 stands for, but that might be what you need. i can't check that on my box as i have no ntfs filesystems but hopefully someone wiser will tell you.

---

### Post by krajni on 2007-01-05
ok so it was because 222 didnt give me read permissions below root level  000 worked problem solved.....however i still dont under stand the whole number thing....i understand how 222 gives you  444 and 555 permisions for files and folders respectively and the first number is for owner second for group third for others, but what i dont know is what exactly are those permissions....how do the number values correlate to  read/write/execute...what would 123 give me?  745? 623? etc etc etc

---

### Post by annda on 2007-01-05
i personally think a sticky post/thread on permissions would be great.

since it doesn't exist, here's a [summary from wikipedia]("http://en.wikipedia.org/wiki/File_system_permissions"):

> With three-digit octal notation, each numeral represents a different component of the permission set: user class, group class, and "others" class respectively.

Each of these digits is the sum of its component bits (see also Binary numeral system). As a result, specific bits add to the sum as it is represented by a numeral:

    * The read bit adds 4 to its total,
    * The write bit adds 2 to its total, and
    * The execute bit adds 1 to its total.

These values never produce ambiguous combinations; each sum represents a specific set of permissions.

These are the examples from the Symbolic notation section given in octal notation:

    * "-rwxr-xr-x" would be represented as 755 in three-digit octal.
    * "-rw-rw-r--" would be represented as 664 in three-digit octal.
    * "-r-x------" would be represented as 500 in three-digit octal.

in simple terms, you decide what permissions you need for a file/directory and then add those 4's 2's and 1's for the owner, group and others and use them as your 3-digit value.

usually you use the chmod command to set permissions, umask (and the subtraction rules) are unique.  so 123 as umask value would mean 654 (owner: rw, group: rx, others: r)  in case of directories and 543 (owner: rx, group: r, others: wx) in case of files.

however, you will normally use permissions with chmod, so forget the subtraction and get used to octal values for specific read/write/execute combinations.

hope this is clear enough and i haven't miscalculated anything.

---

