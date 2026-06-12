---
title: "Question about options with terminal commands"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by darthvivi on 2006-07-02
I'm trying to learn how to use the terminal from this guide: [http://www.ubuntuforums.org/showpost.php?p=399109&postcount=4](http://www.ubuntuforums.org/showpost.php?p=399109&postcount=4)

I'm confused about how options work. If there's two options, say,

-r
and
-f

Can you combine the together and just say "-rf" 
or would you you have to say "-r -f"

Because in the guide, it looks like you can just say -rf to mean -r and -f, which confuses me. Is that how it works?

---

### Post by aysiu on 2006-07-02
Yes, that's how it works.

---

### Post by darthvivi on 2006-07-02
Ok, thanks.

Another question: the mv command has -i as an option, but as far as I can tell, it does absolutely nothing. I'm not asked to confirm anything. What does it do, then?

Also, is there a way to signify a space in a folder name? For instance, I have a folder called "Project Gutenberg" but the space seems to mess things up in the terminal.

---

### Post by aysiu on 2006-07-02
From ```
man mv
``` > -i, --interactive
              prompt before overwrite For folders and files with spaces in them, you can use quotation marks, just as you did in the post above.

---

