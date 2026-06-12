---
title: "editing alias options"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by miesnerd on 2008-04-11
Basically, i want to do some simple things, but I cant figure out where my syntax is wrong, so I';d like a little clarification.
 This isnt a big deal, but for example, I wanted to set ls -mm (which is currently not defined) to give the output for ls -s -S -r -l (how I want things to be displayed certain times). tell me what I did wrong in the terminal:
alias ls -mm= ls -s -S -l -r

when I do that, it returns text stating that it cannot find that option, such as "bash: alias: -s does not exist.

also, so I dont keep asking questions like this, what's a good book that I can buy that will be a reference for all these nitty gritty details in linux? 

Thanks

---

### Post by kellemes on 2008-04-11
> **miesnerd said:**
> Basically, i want to do some simple things, but I cant figure out where my syntax is wrong, so I';d like a little clarification.
 This isnt a big deal, but for example, I wanted to set ls -mm (which is currently not defined) to give the output for ls -s -S -r -l (how I want things to be displayed certain times). tell me what I did wrong in the terminal:
alias ls -mm= ls -s -S -l -r

when I do that, it returns text stating that it cannot find that option, such as "bash: alias: -s does not exist.

also, so I dont keep asking questions like this, what's a good book that I can buy that will be a reference for all these nitty gritty details in linux? 

Thanks

You cannot make aliases with variables I'm afraid..
You can however create an alias without space like ```
ls-mm="ls -s -S -l -r"
```

Edit: [More on aliases from the Gentoo folks]("http://gentoo-wiki.com/TIP_alias").

---

### Post by erginemr on 2008-04-11
+1 to: **alias ls-mm="ls -s -S -l -r"**
or in short: **alias ls-mm="ls -sSlr"**

And to make your aliases permanent between sessions, you can add the same line(s) to the end of your **~/.bashrc** file.

---

