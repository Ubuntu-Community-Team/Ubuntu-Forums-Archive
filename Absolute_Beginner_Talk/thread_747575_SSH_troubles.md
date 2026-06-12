---
title: "SSH troubles"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by parmdeep on 2008-04-06
hi every1, 

i connect to a SSH server using ssh [email]xxxxx@aldgate.cs.ucl.ac.uk[/email]
it then asks for my password, and im connected to the server i can view all my files and use general terminal activities.

im trying to copy a file from the server i have just ssh into, but i cant do it. how do i do it?

also i read that i can view in a window by using place./connect to server/ssh

but for some reason it just locks at tryin to establish a connection am i filling in the options wrong?

thanks in advance

---

### Post by Joeb454 on 2008-04-06
You can use sftp, because it uses the same ports as SSH

You should be able to use this, as long as the server has ftp installed :) Obviously sftp is a secure method of ftp :) Either way it can't hurt to try :)

---

### Post by wormser on 2008-04-06
The places option is easier way to go.  It is hard to know what you are doing wrong with out seeing it.  My guess is you need to add a folder.  Try /home/username.  If that doesn't work then try / or /home.

---

### Post by tamoneya on 2008-04-06
transfer to local computer from server
```
scp xxxxx@aldgate.cs.ucl.ac.uk:/directory/i/want/file ~/MyStuff
```

transfer from local computer to server
```
scp ~/MyStuff/file xxxxx@aldgate.cs.ucl.ac.uk:/directory/i/want 
```

---

### Post by pseudo-random on 2008-04-06
If SFTP isn't available you could SSH in then open the ftp client to put it on an ftp server located with you or 'cat pipe' it to netcat to send it raw to a netcat server listening at home which outputs direct to a file, transferring the file in a roundabout way.

---

### Post by parmdeep on 2008-04-06
i can login sftp using the terminal(it works!!), but i encounter the same problem of how to copy the file? i dont have the option to sftp in places/coonect to a server/ any other ideas

---

### Post by mister_pink on 2008-04-06
Use the scp command above, it should work. Or in nautilus in the address bar just type ssh://aldgate.cs.ucl.ac.uk

---

### Post by Joeb454 on 2008-04-06
sftp works in the current directories by default.

So ```
put *.doc
```
would put all .doc files in your current local directory, into your current remote directory :)

Also see the sftp man page [here]("http://amath.colorado.edu/computing/software/man/sftp.html")

---

### Post by pseudo-random on 2008-04-06
Am I right in guessing you're unfamiliar with a command line file transfer client?
you need to GET the file you want.
It will get put into the local directory you were in when you started SFTP/FTP (default is home)
Sorry if you know this BTW.

---

### Post by parmdeep on 2008-04-06
ok update:

the scp command creates a folder in the server directory called /MyStuff which when i try conenct to it says it doesnt exist but i can see it when i use ls command.

when i use nautilus in the bar i type my user name and password yet it doesnt do anything just get the loading mouse symbol

scp [email]xxxxx@aldgate.cs.ucl.ac.uk[/email]:/directory/i/want/file ~/MyStuff

after using this i get this displayed in the terminal
quotes.csv                        |    55B |   0.1 kB/s | TOC: 00:00:01 | 100%

so i guess i done something correct but the file isnt on my pc and the mystuff folder is in the server but when i try to cd to it it says it doesnt exist.

thanks fro the quik replys


Edit: output:

1 psamra@aldgate% ls
Course Work             Reuters Data Store      thunderbird
Desktop                 badboy.zip              tomcat
My Pictures             desktop.ini             win32
My Received Files       gc15-cw2                workspace
My Sharing Folders.lnk  project
MyStuff                 recycler
2 psamra@aldgate% cd MyStuff
MyStuff: Not a directory
3 psamra@aldgate%

---

### Post by parmdeep on 2008-04-06
@puesdo random, im havin trouble even cd to the right folder as it is called Course Work with the space but when i type in cd Course\ Work it doesnt work 
could you help me help cd to a folder with a space in it?
also does the GET command work just like GET filename?

---

### Post by pseudo-random on 2008-04-06
Try ```
cd Course*
```
wink wink
```
get file.txt
```

---

### Post by parmdeep on 2008-04-06
cd Course* doesnt work :(

damnThatSpaceBar

---

### Post by pseudo-random on 2008-04-06
Bear in mind its case sensitive.
```
cd course*
```
This assumes that course work is a sub-directory of your current directory.

---

### Post by parmdeep on 2008-04-06
sftp> ls
Course Work               Desktop                   My Pictures               
My Received Files         My Sharing Folders.lnk    MyStuff                   
Reuters Data Store        badboy.zip                desktop.ini               
gc15-cw2                  project                   recycler                  
thunderbird               tomcat                    win32                     
workspace                 
sftp> cd Course*
Couldn't stat remote file: No such file or directory
sftp> cd Course Work
Couldn't stat remote file: No such file or directory
sftp> cd /Course*
Couldn't stat remote file: No such file or directory
sftp> cd /Course\ Work
Couldn't stat remote file: No such file or directory
sftp> cd Course\ Work
Couldn't stat remote file: No such file or directory
sftp> 

i have tried all of these combinations and still nothing :(

---

### Post by pseudo-random on 2008-04-06
```
cd "Course Work"
```
Failing that give me your credentials and I'll get it for you. Just kidding.

---

### Post by parmdeep on 2008-04-06
omg finally it worked "" ftw, thank you very much for sticking with me!!! im gonna have to thank you for that one

---

### Post by mister_pink on 2008-04-06
As an aside, it sounds like you typed in the scp command while ssh'ed in to the server, you need to do it locally. Strange that nautilus didn't work though

---

