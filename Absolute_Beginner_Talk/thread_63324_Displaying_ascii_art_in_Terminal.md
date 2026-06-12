---
title: "Displaying ascii art in Terminal"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by cnayak on 2005-09-07
I want to show this piece of ascii art every time I open the terminal. So what file do I edit?

        / \  /\  /\  /\  /\  /\  /
        \/  \/  \/  \/  \/  \/  \/      
        |                        |           H   H  EEEEE  Y   Y
        |                        |           H   H  E      Y   Y
        |                        |           HHHHH  EEE     Y Y
        |                        |           H   H  E        Y
        | __----__      __----__ |       H   H  EEEEE    Y
        |/        \    /        \|
        |          |  |          |                   M   M     AAA       N   N   !!
      --|\     *  /    \     *  /|--               MM MM  A   A      NN  N   !!
     /  | --____--      --____-- |  \            M M M  AAAAA    N N N   !! 
    | (-|         /    \         |-) |               M   M    A   A       N  NN   
     \  |.        \____/        .|  /               M   M    A   A       N   N   ()
      --/                        \--   
       /                          \     
       `--______________________--'          EAT MY SHORTS!!!
          \_                  _/

---

### Post by Nequeo on 2005-09-07
The short answer is .bashrc.  This is a hidden file in your home directory. So you can edit it, even if you can't see it. Try typing 'gedit .bashrc' on the command line - which will be less annoying in the long run than enabling 'view hidden files/folders' in Nautilus.  

The long answer, just in case you can't get it working, is to save the ascii art in a text file in your home directory. Lets assume you called it 'art.txt'.

Just add the line 'cat ~/art.txt' to the bottom of the that file (not changing anything else), and you should be good to go.

Cheers,

---

### Post by cnayak on 2005-09-08
[QUOTE=Nequeo]The short answer is .bashrc.  This is a hidden file in your home directory. So you can edit it, even if you can't see it. Try typing 'gedit .bashrc' on the command line - which will be less annoying in the long run than enabling 'view hidden files/folders' in Nautilus.  

The long answer, just in case you can't get it working, is to save the ascii art in a text file in your home directory. Lets assume you called it 'art.txt'.

Just add the line 'cat ~/art.txt' to the bottom of the that file (not changing anything else), and you should be good to go.

Cheers,[/QUOTE]

 that worked..thanks a lot :)

---

