---
title: "Help with simple copy (cp) command"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Stephen_A on 2006-09-01
Hi, 
I'm asking a very basic question here. I've already searched the documentation but can't fine anything to help. 
  I need to copy a file from an external USB drive to my home directory. The USB drive is: 
     /dev/sda
...and the directory I want to put the file on is: 
/home/stephen
In the LDP it says: 

 cp [OPTION]... SOURCE DEST

Which isn't a lot of help for me. Could someone please tell me what I should type into the terminal? Many thanks. 

Stephen.

---

### Post by slimdog360 on 2006-09-01
cp /dev/sda/filename.xyz /home/stephen

you might need to use sudo in front of that

---

### Post by Stephen_A on 2006-09-01
Hi, 
That looks like it will do the trick. Many thanks. 

Stephen.

---

### Post by cocteau on 2006-09-01
The way to read the helpfiles is that whatever is in captions, i.e. [] is optional, and each word means a seperate white space seperated option, that needs to be there. So if you wanted to copy a directory with all the subdirs as well, the command would be:

cp -R SOURCEDIR TARGETDIR

Hope that helps.

And to slimdog. Shouldn't that quote be 'There's no place like /~'

---

### Post by BaffledMollusc on 2006-09-01
> **Stephen_A said:**
> Hi, 
I'm asking a very basic question here. I've already searched the documentation but can't fine anything to help. 
  I need to copy a file from an external USB drive to my home directory. The USB drive is: 
     /dev/sda
...and the directory I want to put the file on is: 
/home/stephen
In the LDP it says: 

 cp [OPTION]... SOURCE DEST

Which isn't a lot of help for me. Could someone please tell me what I should type into the terminal? Many thanks. 

Stephen.
You probably know this already, but just in case you don't: you don't have to use the command line to copy files. You can drag and drop using the file browser (nautilus).

---

### Post by pufuwozu on 2006-09-01
Actually, /dev/sda isn't a directory so you won't be able to copy from it.

Ubuntu should have auto-mounted the device though so you should be able to do this:```
ls /media/
```And then look for your USB device in the list. Mine is called "UNKNOW_X" but it's usually called something like "usbdisk".

Anyway, because they drive is actually mounted and turned into a directory inside /media/ you should be able to copy from it.```
cp /media/usbdisk/file ~/ # Remember it may not actually be called "usbdisk"
```

---

### Post by Stephen_A on 2006-09-01
Yes I understand that I could use Nautilus but I want to practise using the Terminal. 
  The ls /media/ command shows the USB drive has been auto mounted. There is another little problem: I'm getting an error message:

   cp: missing destination file operand after '/dev/sda/rp-pppoe-3.8/home/stephen'

Could anyone enlighten me what 'missing file operand' I need to put in?

Thanks.

---

### Post by bom28 on 2006-09-01
> **Stephen_A said:**
> 
   cp: missing destination file operand after '/dev/sda/rp-pppoe-3.8/home/stephen'


You must put a space between the source and destination, and as pufuwozu said /dev/sda in not a directory (it's pseudo file with all your usb drive in it), you must use /media/usbdisk, or whatever the name in "ls /media/" is. So you must type :
cp /media/usbdisk/rp-pppoe-3.8 /home/stephen/
also, you don't have to type the full name of files an directories, you just type the beginning and press tab to autocomplete, as a bonus when autocompleting you know the file is there and that there is no typo.
example :
cp /me[TAB]usb[TAB]rp-[TAB]/ho[TAB]st[TAB]
if it doesn't auto complete, press tab again to get a list of possible matches.

---

### Post by Stephen_A on 2006-09-01
This is very useful information for me. Thanks for your time and trouble in replying. 

Stephen.

---

