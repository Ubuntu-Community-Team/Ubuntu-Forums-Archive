---
title: "Apache Message Board"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-26
I have been trying to configure apache....

For the longest time I was configuring the WRONG FILE.

Now that I have the RIGHT file in ubuntu, I need help.

I have installed a message board at /var/www/board

I can NOW point apache at /var/www/board and it opens the index file perfectly, BUT the message board thinks it is at /board and so when the message board calls a file like /board/this.file it can't find it.

I want to point apache at /var/www/board, yet still parse addresses from /var/www.

Any suggestions?  I can't move the message board.

---

### Post by henriquemaia on 2006-05-26
[quote=morequarky]I have been trying to configure apache....

For the longest time I was configuring the WRONG FILE.

Now that I have the RIGHT file in ubuntu, I need help.

I have installed a message board at /var/www/board

I can NOW point apache at /var/www/board and it opens the index file perfectly, BUT the message board thinks it is at /board and so when the message board calls a file like /board/this.file it can't find it.

I want to point apache at /var/www/board, yet still parse addresses from /var/www.

Any suggestions?  I can't move the message board.[/quote] 
Probably you're looking at the wrong place. The problem can be the config files of the board you installed. Check the files where you choose the location of the board on the board folder itself.

---

### Post by morequarky on 2006-05-26
I know there is a howto somewhere on letting USERS have websites like /home/username/www.  I can't find the howto anywhere.

---

### Post by henriquemaia on 2006-05-26
[quote=morequarky]I know there is a howto somewhere on letting USERS have websites like /home/username/www.  I can't find the howto anywhere.[/quote]

For that you just have to enable the module userdir (is it enabled by default?). 

You just have to put things on the folder /home/username/public_html and access it by typing [http://localhost/~username](http://localhost/~username)

Maybe this is not what you meant.

---

### Post by morequarky on 2006-05-26
I'll try that.  I didn't know how to do that.

Hope it works.  That is great.  Just want I need.

My /var is too full and it is a really hassle to repartition the thing.  

Holding files in a public user account file like that will solve all my problems.

---

### Post by henriquemaia on 2006-05-26
[quote=morequarky]I'll try that.  I didn't know how to do that.

Hope it works.  That is great.  Just want I need.

My /var is too full and it is a really hassle to repartition the thing.  

Holding files in a public user account file like that will solve all my problems.[/quote]

I have a more detailed howto on how to get this working. Look here:

[http://ubuntuforums.org/showthread.php?p=1053671#post1053671](http://ubuntuforums.org/showthread.php?p=1053671#post1053671)

---

### Post by morequarky on 2006-05-26
I got it working.  and with the help of a guy on the message board help forum I got everything working great.

---

