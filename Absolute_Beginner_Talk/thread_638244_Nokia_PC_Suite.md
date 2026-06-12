---
title: "Nokia PC Suite"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Fungal Fractoids on 2007-12-11
I found a tutorial on accessing your nokia phone using obextool. So far it has been going successfully but I have a few noob questions about how to use code.

This is where I am up to:

> When we start Obextool we can see this error message:

It seems, that your device does not support the memory status feature.
Memory status will be disabled

To solve this problem we have to set some values on obextool.cfg:

    ```
sudo gedit /etc/obextool.cfg

    set ObexConfig(config,memstatus) 0
    set ObexConfig(config,filemove) 0
```

I assume this means I use that sudo command to open gedit, then copy and paste the lines underneath it into the blank text file that opens, is that about right? Because I did that and am still getting the error message when I open the app.

Same goes for this bit:

> Another error message that we can see is:

FIle '/FileName/' could not be uploaded to 'E:/Path'!
Please check your file permissions.

To solve it:
```

    sudo gedit /etc/obextool.cfg

    set ObexConfig(config,dir_slash) 1
```

I wasn't even seeing this error message, but was just doing the same as above- copying into the text file gedit brings up.

Can anyone see what I am doing wrong?

---

### Post by stego_s_aurus on 2007-12-11
Check to make sure those lines that youre cutting and pasting in dont already exist in the files that you are editing! They Might be there already, but with a different setting than what you are trying to set. Unless you remove the existing line (or comment it out) it may still be encountering the first line and ignoring what you pasted in.

For example:
 before pasting in the line that reads 
   set ObexConfig(config,memstatus) 0
do a search for 
  set ObexConfig(config,memstatus)

because who knows: you may already have a line that reads
   set ObexConfig(config,memstatus) 1

in the file already!

---

### Post by Fungal Fractoids on 2007-12-12
Yeah it ends up that the obextools.pfg was in another directory anyway, I just had to alter the values already there. Works fine now :)

---

