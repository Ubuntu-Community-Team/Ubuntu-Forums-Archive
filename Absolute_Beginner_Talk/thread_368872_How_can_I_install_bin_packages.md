---
title: "How can I install bin packages ??"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-02-23
I downloaded some bin packages when i was looking for new softs. online , such as RealPlayer 10 , the manual says :
- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

I pointed the bash to the folder where the file locates , and then wrote 
> chmod a+x RealPlayer10GOLD.bin  
but it replied :
> bash: chomd: command not found
then tried typing :
> sudo chomd a+x RealPlayer10GOLD.bin
and the bash replied :
> sudo: chomd: command not found

what can i do to install the file properly ?
step by step , plz (if u can)

thanks in advance

---

### Post by Maestro23 on 2007-02-23
In the directory where the file is:

> chmod +x filename.bin

./filename.bin



---

