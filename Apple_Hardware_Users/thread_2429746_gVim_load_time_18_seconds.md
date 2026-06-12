---
title: "gVim load time 18 seconds?"
date: 2019-10-22
forum: Apple Hardware Users
---

### Post by keith562 on 2019-10-22
Hi,


I had a 19.04 running nicely on an old MacBook Air. I wiped it down and installed 19.10 on it, because I was curious. Everything ran fine... excpet gVim.


With no .vim folder it was all okay, but as soon as I put the same .vim folder I had used on 19.04, into my home folder and ran gVim, it took 18 seconds to load where it had been almost instant under 19.04. When I ran vim from inside a terminal, it was once again near instant.


Anyway, I wiped it all down again and put 19.04 back on the Macbook and gVim was back to opening like greased lightning.


I am pretty new to Linux, but I would like to know what would be likely to make for such a delay in the load time for the graphical version of this app between 19.04 and 19.10


I liked 19.10, what I saw of it, but if it makes my editor of choice unusable, then I will have to stick with 19.04, which is a shame.


Keith.

---

### Post by wildmanne39 on 2019-10-22
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by zimbuf on 2019-10-22
Might be inside of a snap. Try building from source from the [website]("https://www.vim.org/download.php#unix").

```
sudo apt-get install build-essential && sudo apt-get build-dep vim
```

before you go-go, and you'll be good

---

### Post by keith562 on 2019-10-23
Okay, whilst I have no problem giving this a try, I should now perhaps make it clear that Linux and I are relatively new friends, and a lot of what many people take for granted, it still arcane knowledge for me.

        ```
sudo apt-get install build-essential && sudo apt-get build-dep vim
```
I think I understand this command line suggestion, but could we just clarify what use this will be to me? I am under the impression that gVim is just a graphical front end for Vim, and as I said Vim, when run from the command line, is lightning fast. It is only when invoked as gVim that the crazy delay kicks in.

Unless my limited understanding it causing me to misunderstand, your command will rebuild from scratch the part that is actually working.

Am I missing somthing obvious here?

Thanks for taking the time to offer help.

Keith.

---

### Post by PaulW2U on 2019-10-23
> **keith562 said:**
> Am I missing somthing obvious here?
I saw your original post but as I was unable to offer any help I decided not to reply.

I'm pretty sure that the implication you had installed vim from a snap or that you (re)install vim by building from source was not the best advice that you could be given at this stage.

---

### Post by keith562 on 2019-10-23
Okay, I will hold back on that then and see what else I can find out.
This is nothing if not fun.
Thank god I am retired and can spend time tinkering like this... :-)

Keith.

---

### Post by orjanp2 on 2019-10-24
I have the same problem. If I remove the .gvimrc file, it works fine. Putting it back again, it takes a long time to load. The .vimrc and .vim/ folder does not make a difference, onlu the .gvimrc file.

---

### Post by keith562 on 2019-10-24
I went away and played with my problem, and actually found the solution. It is really quite trivial, but I thought the decent thing to do would be just to stick a note on the thread, in the unlikely event that someone else stumbles into the same issue as I did.

When running 19.04, I used gVim as my editor and I found the toolbar of icons to be an annoyance and saw in the settings that I could tern them off with;

```
set guioptions-=T

```

With that added to my vimrc file gVim opened immediately with no annoying icons.

I did a clean install of 19.10, I copied my .vim folder over and that was when gVim took 18 seconds to boot.

When I deleted the 'set guioptions' line, gVim went back to loading instantly.  I dont know if all the settings options would cause a similar problem, but this one caused mine.

For what its worth I now apply the 'set guioptions' after the program is running with;

```
"imap <leader>z <esc>:set guioptions-=T<cr>
"nmap <leader>z :set guioptions-=T<cr>

```
It is not quite as convenient, but I am not sufficiency skilled to do any better.

Keith.

---

### Post by orjanp2 on 2019-10-27
Found the same. Turning off the icon toolbar in gvimrc file with ```
set guioptions-=T
``` is what causes the slow loading.

---

