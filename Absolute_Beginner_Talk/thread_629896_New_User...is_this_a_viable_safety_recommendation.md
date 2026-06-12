---
title: "New User...is this a viable safety recommendation???"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-12-02
Hi all,
I am a newb (isn't it obvious). I have just started doing the online Linux course to assist in the winDOSE-LINUX transfer. Noticed in lesson 6
? Does this help prevent the malicious rm....crap that is going on?

[COLOR="Blue"][I]Adding aliases to the .bashrc file

Well, you now have '.bashrc' open in 'pico' or your new, favorite text editor. It would be a good idea to add this line first, so you know what you've done.

    # my personal aliases 

The pound sign (#) tells the shell not to read that line. It's known as a 'comment'. Then you would add:

    cp='cp -v -i'

on the next line write:

    rm='rm -i' 

so we don't send anything into byte heaven without a warning. And finally

    mv='mv -i' 

So you're aliases will look like this

    # my personal aliases
    alias cp='cp -v -i'
    alias rm='rm -i'
    alias mv='mv -i'

Save that file and logout and login again. Now you have a safer, easier shell environment. As you get more proficient at Linux, you can add more aliases as you see fit.

Now your shell's ready to go. If you type logout and then login again, your aliases will work. There is also a short-cut. If you type:

    source .bashrc 

your aliases will be ready to go. [/I][/COLOR]

Is this not required in Gutsy or is it an increased safety thing for newbs like myself to act as a safety net.  Please advise accordingly. Thanks

Nigel

---

### Post by hogwartsnigel on 2007-12-02
I think I have found my own answer..please though if I'm wrong let me know...Further in lesson 6 they mention that anything that has "-f" avoids the alias so that means that "rm-rf" wouldn't solicit the help? Oh well I'll keep reading

Nigel

---

### Post by Hospadar on 2007-12-02
Yeah, the "-i" option prompts you whether or not you want to delete every file.

As for the "-f" option, yes, it will overwrite the -i, but you never *need* to you -f, it's just sometimes convenient if you're deleting a ton of write-protected files that you _**know**_ you want to delete.

So if you see a command with the "f" option, just take the f out.  for example "rm -rf" does the same thing as "rm -r" it will just sometimes prompt you before deleting certain files.

So bottom line, _yes_ those aliases may help you, but I think that a lot of the time they will slow you down.  If you see unexplained rm, mv, or cp commands and don't know if they are safe, just ask someone here and you'll be able to get a straight answer.

rarely should things just be deleted.  If you are suspicious about an rm command, try just renaming or moving the files, as this will have the same effect, but is easy to reverse if it turns out to be unsafe.

---

### Post by siciliancasanova on 2007-12-02
Since you're in your .bashrc file anyway, this one WILL be helpful in my opinion.

Just add this line to the bottom of the file

```
export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '
```

It will change the colors of the text for the heirarchy, those are just ASCII colors so if you want to change the colors just adjust the numbers right before the "m's"

---

### Post by hogwartsnigel on 2007-12-02
woooaaahhh!
Thanks sicillian, I knew it was risky posting random thoughts whilst learning on here....LOL
[COLOR="Blue"]export PS1='\[\033[0;35m\]\h\[\033[0;33m\] \w\[\033[00m\]: '[/COLOR]
and the answer is 42!? I'm up to lesson 9....god I haven't even worked out how to network yet....LOL. Thanks though I'm sure I'll use it.
Thanks Hospadar, I know these forums are great, I got a little freaked at the sticky note on malicious code after one contained stuff that equalled the rm command but was in a sum form....I wouldn't have seen it., and when you are so new you rely on command prompt assistance. Luckily for us all 99.99% of people are the best sort you could meet.
For my part I want to learn as much as I can and recommend all newbs do what they can, this learning tool is painfully basic but god I need it.

Thanks to you both

Nigel

---

