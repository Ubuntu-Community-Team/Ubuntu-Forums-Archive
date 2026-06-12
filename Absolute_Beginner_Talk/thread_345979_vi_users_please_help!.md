---
title: "vi users please help!"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by jtibau on 2007-01-25
Could someone explain me why vi commands work differently now in edgy.
I got used to using vi on the shell for fast editing of system files, writing scripts in bash and perl. Edgy's vi behaves differently, specially regarding the directional keys. I often use ssh to login to a dapper server, I get mixed up with the behaviour and it is a pain in the a..
Perhaps an explanation would at least ease my suffering, however if there is a way to fix it, it would be much much better :)

---

### Post by DSn0wMan on 2007-01-25
I am not sure if anything changed. I usually dont touch the arrow keys in VI (the do weird things in Unix).

ESC + K = move cursor up
ESC + J = move cursor down
ESC + L = move cursor right
ESC + H = move cursor left

---

### Post by jtibau on 2007-01-25
maybe I should learn to not use them arrow keys... Anyway I've noticed this kind of different behaviour, all in edit mode:

dapper:
backspace erases previous character
edgy:
backspace doesn't erase previous character. It sortof sets the character to a replaceable state (don't know how to explain it better) but if you type something it will replace the character that was meant to be erased. Thus the only way of erasing is the del key or in command mode. I did use backpace a lot though.

dapper:
I also used to move the prompt in edit mode using the arrow keys.
edgy:
I does some weird stuff like you said.

---

### Post by DSn0wMan on 2007-01-25
Ya, it seems like the dapper version worked somewhat like bash. The version I have in edgy seems to behave like the vi on our AIX (Unix ksh) machines at work.

Maybe there is some environment variable that needs to be changed, or a wierd symlink that points somewhere different in edgy.

---

### Post by weresheep on 2007-01-25
Hello,

It seems that in Edgy, Ubuntu only defaults to installing vim-tiny package which offers a subset of features. To get the features you want back, it seems you have to install the vim-full package.

See [here]("http://www.digitalblueprint.co.uk/articles/2006/11/23/vi-arrow-keys-in-ubuntu-edgy/") for more information.

I also recommend running 'vimtutor' once vim-full is installed as it seems you are nor making the most of VIM/vi's features. Moving the cursor around in EDIT mode is not optimal when there are many powerful commands for positioning the cursor in NORMAL mode.

Anyway, I hope that helps.

-weresheep

---

### Post by jtibau on 2007-01-25
I will gladly take your advice :) I'm apt-getting vim-full right now.

---

### Post by DSn0wMan on 2007-01-25
> **weresheep said:**
> Hello,

It seems that in Edgy, Ubuntu only defaults to installing vim-tiny package which offers a subset of features. To get the features you want back, it seems you have to install the vim-full package.

See [here]("http://www.digitalblueprint.co.uk/articles/2006/11/23/vi-arrow-keys-in-ubuntu-edgy/") for more information.

I also recommend running 'vimtutor' once vim-full is installed as it seems you are nor making the most of VIM/vi's features. Moving the cursor around in EDIT mode is not optimal when there are many powerful commands for positioning the cursor in NORMAL mode.

Anyway, I hope that helps.

-weresheep

Thanks for the tip. Everything works as expected now.

---

