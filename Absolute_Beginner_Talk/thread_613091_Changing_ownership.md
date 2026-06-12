---
title: "Changing ownership"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by rafeg on 2007-11-14
Could someone help with this please.   I am using 7.10  with great success so far but have come up against a problem re ownership of a file.    
         I want to send it to a different account I have set up for confidential documents and tried changing ownership in a terminal using the chown command:

        sudo chown <owner> <filename.odt>
  
        I get the message <filename> no such file or directory.  I have tried this in several forms but always the same result.  My Linux books and several web sites have shown the same syntax so I'm a bit stuck!    Any help would be much appreciated.

                                                                 Thanks

---

### Post by Dr Small on 2007-11-14
```
sudo chown *user* */path/to/filename.odt*
```

---

### Post by carlosjuero on 2007-11-14
> **rafeg said:**
> Could someone help with this please.   I am using 7.10  with great success so far but have come up against a problem re ownership of a file.    
         I want to send it to a different account I have set up for confidential documents and tried changing ownership in a terminal using the chown command:

        sudo chown <owner> <filename.odt>
  
        I get the message <filename> no such file or directory.  I have tried this in several forms but always the same result.  My Linux books and several web sites have shown the same syntax so I'm a bit stuck!    Any help would be much appreciated.

                                                                 Thanks
Are you using the < and > symbols in the command line? (Just wondering).

In any case, try this
```

sudo chown newowner:newownergroup ./filename.odt

```

(Edit: this assumes you are in the same folder as the file, otherwise replace the ./ with the full path)

---

### Post by rafeg on 2007-11-14
Wow! What quick responses.  Thanks very much.  I've had to leave Ubuntu for the time being as my wife
wants to use W******* !!        But I'll try your suggestions a.s.a.p. and see how I go.

---

### Post by rafeg on 2007-11-15
I Tried your instructions, thanks for them, :confused: and got the message that ownership had changed (I was not aware how important it is to get the EXACT path correct. (Coming from Windows, of course, where you don't need to think!).  I prefer thinking but its taking time to adjust.
           However, the file remains in my general user account and can still be seen by un-authorised eyes.  What I was trying to do was move the whole document lock stock and barrel to a private user account where it will be inaccesible except to that user.  Obviously I am not using the correct command.  Any further help on this please?

---

### Post by hyper_ch on 2007-11-15
Well, you can make sure, other users than you cannot access it. For this, there are two steps included:

(1) Assign file ownership to your user and your usergroup (assuming your username is "rafeg"):

```

sudo chown rafeg:rafeg /path/to/filename.odt

```

(2) Strip other users of the rights do do anything with the file:

```

sudo chmod 0700 /path/to/filename.odt

```

So only the user "rafeg" can still read, write and execute that file. Every other user (except for the root use, who has god-like powers on a linux box, no one can do anything with that file). Other users aren't permitted to access that file in anyway, but it will still be visible to them.

---

### Post by rafeg on 2007-11-15
Thanks for that help.  I succeeded in changing permissions and now cannot open the folder.  How do I reverse the process?   The folder is a "Dummy" set up to practice the process of moving and manipulating etc.  I now want to re-instate my permissions and delete the folder but it won't let me in of course.  Sorry if I'm being thick about this but Linux is very different from W******** and I've much to learn!!
                 Thanks to all who have offered help.

---

### Post by g2g591 on 2007-11-15
sudo chmod 777 foldername . this will allow anyone to access it. Incase you're wondering, the first digit is the permissions for its owner 2nd permissions for the group of the owner (you can belong to many groups at once) the third digit for everyone else

---

### Post by rafeg on 2007-11-15
thanks g2g591.  I'd tried this without success.  Why?  I'd forgotten that darned Path again.  Ok now though.  I suppose I'll eventually get the correct procedure into my thick nut!!

                                                 Thanks again

---

