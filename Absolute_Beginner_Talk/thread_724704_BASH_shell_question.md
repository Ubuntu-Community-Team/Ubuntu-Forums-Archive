---
title: "BASH shell question"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Xephyrind on 2008-03-14
Hello,

I was reading the shell manual with this command in terminal

yelp man:bash

I have 2 questions.

1.Near the top it says:
Synopsis
bash [option]... 

What does the word synopsis mean in this case. I looked up dictionary and can't find a good definition for the word used in this sense.

2. I executed the command: 
bash -D 

which is listed on there, to see what's going to happen. Well, My screen went from

xephyrind@xephyrind-desktop:~/Desktop$ bash -s
xephyrind@xephyrind-desktop:~/Desktop$ bash -D

to

bash-3.2$ 
bash-3.2$ bash -D
bash-3.2$ hello world
bash-3.2$ bash -i hello.txt
bash-3.2$ shellopts
bash-3.2$ ls
bash-3.2$ :q

In short, it went from receiving command of:
xephyrind@xephyrind-desktop:~/Desktop$

to NOT receiving any command of:
bash-3.2$ 

I was wondering if this is suppose to be this way? If it is suppose to behave like that. What command do I use besides the CTRL-C to bring it back to the receiving command proper form? Not sure if I've made myself clear. Thanks for reading and helping!

---

### Post by Joeb454 on 2008-03-14
I'm not entirely sure what bash -s or bash -D do, I'd assume it runs bash on top of itself ;)

If Ctrl+C brings you back to your default prompt, just do that :)


And synopsis in that context is just a brief description of what bash is, and options you can run after bash :)

---

### Post by Xephyrind on 2008-03-14
Thanks Bro!!!~... well Somebody plz answer that bash -D does and how to go back to the old screen without forcing it with CTRL-C QQ....

---

### Post by Joeb454 on 2008-03-14
What happens if you just type ```
exit
``` 
Does that work?

---

### Post by jdong on 2008-03-14
> **Xephyrind said:**
> 

What does the word synopsis mean in this case. I looked up dictionary and can't find a good definition for the word used in this sense.


**Synopsis** means summary in this case. A one-sentence description of what the command does.
> 

2. I executed the command: 
bash -D 



Bash is going to have a lot of random flags that only make sense to shell script debuggers. I wouldn't recommend fretting too much about it.

---

### Post by bodhi.zazen on 2008-03-14
The flags are explained later in the man pages :

>        -s        If  the -s option is present, or if no arguments remain after
                 option processing, then commands are read from  the  standard
                 input.   This  option  allows the positional parameters to be
                 set when invoking an interactive shell.

       -D        A list of all double-quoted strings preceded by $ is  printed
                 on  the standard output.  These are the strings that are sub&#8208;
                 ject to language translation when the current locale is not C
                 or  POSIX.   This  implies the -n option; no commands will be
                 executed.

If you do not understand the flags, you do not need them.

If you enter the command ```
bash
```you start a new shell in the same terminal. Type exit to return to the original shell.

To see the utility of flags, try a less complex command, like ls

man ls

---

### Post by handydan918 on 2008-03-15
> **Xephyrind said:**
> Thanks Bro!!!~... well Somebody plz answer that bash -D does and how to go back to the old screen without forcing it with CTRL-C QQ....


From the bash man page....
-D        A list of all double-quoted strings preceded by $ is  printed
                 on  the standard output.  These are the strings that are sub&#8208;
                 ject to language translation when the current locale is not C
                 or  POSIX.   This  implies the -n option; no commands will be
                 executed.

---

### Post by Wolfan on 2008-03-15
To answer your other question, Synopsis is basically another word for explination, or short form of.  So if I give you a synopsis of *Moby Dick* I would basically write a few paragraphs or pages about Ishmael and the Captain and the Whale, without telling you every little detail.

---

### Post by handydan918 on 2008-03-15
> **bodhi.zazen said:**
> The flags are explained later in the man pages :



If you do not understand the flags, you do not need them.

If you enter the command ```
bash
```you start a new shell in the same terminal. Type exit to return to the original shell.

To see the utility of flags, try a less complex command, like ls

man ls
This is a new one to me, as well. But your assertion that typing exit will return you to a standard bash shell aears to be incorrect, at least in a terminal emulator (konsole). 

> -D        A list of all double-quoted strings preceded by $ is  printed
                 on  the standard output.  These are the strings that are sub&#8208;
                 ject to language translation when the current locale is not C
                 or  POSIX.   This  implies the -n option; no commands will be
                 executed.

"No commands will be executed" apparently includes the usual list of suspects like pwd, ls, and ummm....exit.
Or am I missing something?

:confused:

---

### Post by iansane on 2008-03-15
I can't imagine trying to understand BASH from a man page. Those things are so frustrating to understand because they don't use complete sentences and are lacking in indepth explainations and examples. Not that I'm condoning downloading copyright materials but there are a lot of Bash and shell scripting ebook torrents out there if you google for them.

---

### Post by Xephyrind on 2008-03-15
> **Joeb454 said:**
> What happens if you just type ```
exit
``` 
Does that work?

nope XD

---

### Post by Xephyrind on 2008-03-15
> **iansane said:**
> I can't imagine trying to understand BASH from a man page. Those things are so frustrating to understand because they don't use complete sentences and are lacking in indepth explainations and examples. Not that I'm condoning downloading copyright materials but there are a lot of Bash and shell scripting ebook torrents out there if you google for them.


I totally agree with you. Now the question is do you have a good  title/book with lots of good and clear explanation AND great obvious examples? I'd really appreciate it if you can give me a good one :P

---

### Post by Xephyrind on 2008-03-15
Thanks to everyone's generous replies. I appreciate it a lot. I have found out how to get out of the NOT receiving command mode. It can be done by simply doing CTRL-D. I do not know what CTRL-D does exactly in bash. I just basically smashed random keys together "Barbarian style makes the world go around". Then it all of the sudden went back to the good old receiving command mode described in my original post. Thanks :). Hope this helps someone out and hopefully one of the pros will be generous enough to enlighten me what CTRL-D means in bash shell really haha :)

---

### Post by iansane on 2008-03-15
Sorry Xephyrind I can't tell you the link but  One good book is "Linux Shell Scripting With Bash" by: Ken O. Burch. Orielly put out one called "The Bash Cookbook" and you'll find several others if you google for them. Some where there are some Bash video tutorials too but I can't tell you where. Just search for them :-)

---

### Post by jdong on 2008-03-15
CTRL+D is the end-of-file character. When bash, and most programs that take input from the command line, see this character, they assume that you're done inputting and therefore they close.

---

### Post by ghostdog74 on 2008-03-15
please see the link in my sig for learning bash

---

### Post by Xephyrind on 2008-03-15
> **ghostdog74 said:**
> please see the link in my sig for learning bash

hmm Let me check it out and thank you :)

---

### Post by Xephyrind on 2008-03-15
> **iansane said:**
> Sorry Xephyrind I can't tell you the link but  One good book is "Linux Shell Scripting With Bash" by: Ken O. Burch. Orielly put out one called "The Bash Cookbook" and you'll find several others if you google for them. Some where there are some Bash video tutorials too but I can't tell you where. Just search for them :-)


Hi I am just curious. I don't really understand internet laws. Is it against the law to post links linking to other places such as an online tutorial? I am wondering because you said that you can't tell me where to look for the bash video tutorials. It seems like posting links to other places is against the law. Just wondering so I don't get into trouble or get banned thanks :)

---

### Post by Xephyrind on 2008-03-15
> **jdong said:**
> CTRL+D is the end-of-file character. When bash, and most programs that take input from the command line, see this character, they assume that you're done inputting and therefore they close.

Thank you! I sincerely appreciate your assistance. so CTRL+D is like a command saying this is the end~DONE. Hmm... cool! How did you learn those things QQ.... I don't mind being n00b... but I don't want to be THIS noob lol >.<lll

---

### Post by Xephyrind on 2008-03-15
> **ghostdog74 said:**
> please see the link in my sig for learning bash

Hope you don't mind me adding you to my buddylist, I did it because you signature is very RESOURCEFUL lol XD >.<lll~~!

---

### Post by jdong on 2008-03-15
> **Xephyrind said:**
> Hi I am just curious. I don't really understand internet laws. Is it against the law to post links linking to other places such as an online tutorial? I am wondering because you said that you can't tell me where to look for the bash video tutorials. It seems like posting links to other places is against the law. Just wondering so I don't get into trouble or get banned thanks :)

No, posting links to an online tutorial is certainly legal and everyone is more than welcome to do so.

The particular link iansane posted last time, that I removed, was a link to a torrent with 10 different pirated ebooks, and linking to pirated content is against forum policies.

---

### Post by Xephyrind on 2008-03-15
> **jdong said:**
> No, posting links to an online tutorial is certainly legal and everyone is more than welcome to do so.

The particular link iansane posted last time, that I removed, was a link to a torrent with 10 different pirated ebooks, and linking to pirated content is against forum policies.

Oh~ Now so I just somehow have to get iansane to read this message and simply post the titles that he liked so I could purchase them on Amazon or something. Anyway I can contact him via this forum? I am asking this because I doubt that he's going to be back anytime soon to read my post here haha~ Also I am a big n00b in this forum so I suspect that there are some features I can use which I just don't know how ~

---

### Post by Xephyrind on 2008-03-16
> **jdong said:**
> No, posting links to an online tutorial is certainly legal and everyone is more than welcome to do so.

The particular link iansane posted last time, that I removed, was a link to a torrent with 10 different pirated ebooks, and linking to pirated content is against forum policies.

OMG I just noticed your Icon is an Arclite Siege Tank! Ready for StarCraft II?!?!?!? lol just kidding a bit off-topic but meh ~ >.<lll

---

### Post by iansane on 2008-03-16
> **Xephyrind said:**
> Hi I am just curious. I don't really understand internet laws. Is it against the law to post links linking to other places such as an online tutorial? I am wondering because you said that you can't tell me where to look for the bash video tutorials. It seems like posting links to other places is against the law. Just wondering so I don't get into trouble or get banned thanks :)

Sorry, I had to edit my post. The forum rules will not allow me to post links to the actual torrent files because YES it is illegal (in the US and maybe some other countries)  to copy or download copyrighted material. The authors and publishers are trying to make money off selling their books and they loose money when people copy it illegally. The strange thing is that while know one condones this, I would bet that the main use of programs such as bit torrent and azerus is downloading copyrighted music, movies, software, and ebooks. Everyone that I know is doing it, so it's up to you to make your own decision as to the morality of it.

Even as someone who is not totally innocent, I agree that the forum should not allow it. It's not something that should be allowed to run rampant.

---

### Post by Xephyrind on 2008-03-17
> **iansane said:**
> Sorry, I had to edit my post. The forum rules will not allow me to post links to the actual torrent files because YES it is illegal (in the US and maybe some other countries)  to copy or download copyrighted material. The authors and publishers are trying to make money off selling their books and they loose money when people copy it illegally. The strange thing is that while know one condones this, I would bet that the main use of programs such as bit torrent and azerus is downloading copyrighted music, movies, software, and ebooks. Everyone that I know is doing it, so it's up to you to make your own decision as to the morality of it.

Even as someone who is not totally innocent, I agree that the forum should not allow it. It's not something that should be allowed to run rampant.

hmm I aghlee. seeing rampant as it already is without permission, imagine what it will become once it is permitted lawlz XD

---

