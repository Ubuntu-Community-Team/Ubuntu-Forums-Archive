---
title: "What is wrong with me? (command line noob)"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by handyguy33 on 2006-09-21
I recently installed Ubuntu on my PC at home. I'm very pleased with it as an OS. However, I have hit a brick wall in usage. I have two unrelated problems...Ubuntu doesn't detect my modem (an Intel 536ep)and I put a couple of (linux) games on my desktop read the instructions for installation, tried it and got nowhere. Now I am a complete newbie with the terminal window and command line. I have been reading every bit of material that has to do with my problems. I always type exactly what the instructions say. And I always get either "bad command" or "file not found" as a response. Am I stupid or something? Why can't I get anything to work in the terminal?

---

### Post by empcrono on 2006-09-21
> **handyguy33 said:**
> I recently installed Ubuntu on my PC at home. I'm very pleased with it as an OS. However, I have hit a brick wall in usage. I have two unrelated problems...Ubuntu doesn't detect my modem (an Intel 536ep)and I put a couple of (linux) games on my desktop read the instructions for installation, tried it and got nowhere. Now I am a complete newbie with the terminal window and command line. I have been reading every bit of material that has to do with my problems. I always type exactly what the instructions say. And I always get either "bad command" or "file not found" as a response. Am I stupid or something? Why can't I get anything to work in the terminal?

I know this wont solve stuff imdeiatly but, its like a mental block at first. (at least for me it was) keep at it and u will start to understand why a command is written a certain way and how it relates to u comp. in the meantime u should post what game your trying to install and the steps u took. this applies to all programs. also if you can find a deb form of the game and stuff use those. type in the name of the game then type in ubuntu and see then download it and right click install (in those cases) just some tips

---

### Post by benfindlay on 2006-09-21
If the modem is software then you're gonna have problems with it. No idea how to solve that I'm afraid as I've never tried to instal a modem.

With regards to the games, what have you downloaded? Are they debs/source-code/tar balls?

If theyre tar balls then you need to extract, configure, make and make install them. A bit more info would help us to answer the questions, like the exact file names of the games you're trying to run

Cheers

---

### Post by TLE on 2006-09-21
Please specify! What games have you been trying to install and which commands  have you entered, and which one is the first one that gives an error ?

Also ... to get better support, please read 
"Section II - Technical Support Policies:
When asking for technical support:" of the [guidesline]("http://ubuntuforums.org/index.php?page=policy")
Specially the part about informative titles

---

### Post by handyguy33 on 2006-09-21
Thanks for the support...That was quick! I'll keep up reading and trying stuff out. The games I got were Sauerbraten and X-Racer. And yeah, the modem is soft (oh well, looking for hardware modem...wish we had broadband out here in the stix).

---

### Post by Tomosaur on 2006-09-21
XRacer is in the repositories - thus in the terminal, you should type:
sudo apt-get install xracer

---

### Post by MrHorus on 2006-09-21
> **handyguy33 said:**
> And I always get either "bad command" or "file not found" as a response. Am I stupid or something? Why can't I get anything to work in the terminal?

Rather than rote memorisation, read a good shell guide or howto so that rather merely copying and pasting, you understand exactly what you are typing and why.

If you understand about paths, commands and arguemnts then you will understand why something is a bad command and why a file is not found.

---

### Post by 3rdalbum on 2006-09-21
X-racer is incredibly boring... try something like Planet Penguin Racer or Tuxcart, both of which are available from the Synaptic Package Manager, so you don't need to compile them from source.

(note: The reason why you got errors with your downloaded source code was because you haven't installed the build-essential package from Synaptic).

---

### Post by Brunellus on 2006-09-21
> **handyguy33 said:**
> I recently installed Ubuntu on my PC at home. I'm very pleased with it as an OS. However, I have hit a brick wall in usage. I have two unrelated problems...Ubuntu doesn't detect my modem (an Intel 536ep)and I put a couple of (linux) games on my desktop read the instructions for installation, tried it and got nowhere. Now I am a complete newbie with the terminal window and command line. I have been reading every bit of material that has to do with my problems. I always type exactly what the instructions say. And I always get either "bad command" or "file not found" as a response. Am I stupid or something? Why can't I get anything to work in the terminal?
you are probably not stupid.  however, you are also probably doing more work than you need to.

Many Linux games are already packaged in the repositories and are easily installable.  Follow this guide:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

For some help in getting started learning about the shell, go here

[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

---

### Post by pheonix991 on 2006-09-24
I'm in the same boat, and that monkeyblog site is gone I think.

---

### Post by slimdog360 on 2006-09-24
check my sig for a guide

---

