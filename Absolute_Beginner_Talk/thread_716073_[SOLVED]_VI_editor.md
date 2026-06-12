---
title: "[SOLVED] VI editor"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by cybo on 2008-03-05
I'm using VI at work. I'm trying to switch windows. Say I have screen sepearated, on top I have a one.c file and on the bottom I have a two.c file. How would I switch the windows (make two.c on top and one.c on the bottom)? I looked through the manual and is says that I have to use CTRL + W + J (K, H, L) but it didn't work. Can anyone help?

Please keep in mind I'm new to many things

---

### Post by bill516 on 2008-03-06
Page 197, Lamb & Robbins "Learning the vi Editor" (O'Reilly) say:

"...the :spit command will create a new window, and then you use the ex command :e filename to edit a new file in the new window.  ... CTRL-W CTRL-W will let you switch back and forth between windows."

They also say that both windows then share a bottom window (single line, essentially) for ex commands.

If the essence of your problem is that you have your programs in the "wrong" windows, can you simply open topfile.c first, then issue the :split command and then open bottomfile.c?

Perhaps someone else has done multi-window editing in vi or vim, I have not.  But I did try what I am suggesting and it seemed to work.  I did not see any way to "flip" my windows once I had made the initial split.

I assume you know that Gutsy includes a very nice vim tutor.  Just open the terminal and do vimtutor.  That got me started very nicely.

And if you are new and you are going to be using vi (my situation) a copy of Robbins "vi Editor Pocket Reference" (O'Reilly) is really invaluable.  It is very small and you can carry it with you.

Hope this helps!

---

### Post by cybo on 2008-03-06
Thanks. At least I know that it is impossible to "flip" windows. It is strange though becasue the file I found online says that it is possible. I can't find the link now. But as soon as I find it I will post it.

---

### Post by cybo on 2008-03-07
> **bill516 said:**
> Page 197, Lamb & Robbins "Learning the vi Editor" (O'Reilly) say:

"...the :spit command will create a new window, and then you use the ex command :e filename to edit a new file in the new window.  ... CTRL-W CTRL-W will let you switch back and forth between windows."

They also say that both windows then share a bottom window (single line, essentially) for ex commands.

If the essence of your problem is that you have your programs in the "wrong" windows, can you simply open topfile.c first, then issue the :split command and then open bottomfile.c?

Perhaps someone else has done multi-window editing in vi or vim, I have not.  But I did try what I am suggesting and it seemed to work.  I did not see any way to "flip" my windows once I had made the initial split.

I assume you know that Gutsy includes a very nice vim tutor.  Just open the terminal and do vimtutor.  That got me started very nicely.

And if you are new and you are going to be using vi (my situation) a copy of Robbins "vi Editor Pocket Reference" (O'Reilly) is really invaluable.  It is very small and you can carry it with you.

Hope this helps!

this is what i was talking about
[http://www.vim.org/htmldoc/usr_08.html#08.5](http://www.vim.org/htmldoc/usr_08.html#08.5)
does it work for anyone?

---

### Post by Cypher on 2008-03-07
Works perfectly for me with the following version of VIM installed
```

~$ dpkg -l | grep vim
ii  vim-common                                 1:7.1-056+2ubuntu2                   Vi IMproved - Common files
ii  vim-tiny                                   1:7.1-056+2ubuntu2                   Vi IMproved - enhanced vi editor - compact v

```

---

### Post by cybo on 2008-03-07
> **Cypher said:**
> Works perfectly for me with the following version of VIM installed
```

~$ dpkg -l | grep vim
ii  vim-common                                 1:7.1-056+2ubuntu2                   Vi IMproved - Common files
ii  vim-tiny                                   1:7.1-056+2ubuntu2                   Vi IMproved - enhanced vi editor - compact v

```

Works for me too. Apparently I wans't pressing the shift key.

---

### Post by bill516 on 2008-03-09
We all learned something!  Special thanks to Cypher or showing me a nity little maneuver I did not know could be done!

---

