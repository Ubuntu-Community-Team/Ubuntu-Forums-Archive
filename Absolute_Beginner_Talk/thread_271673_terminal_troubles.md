---
title: "terminal troubles"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-05
hello

do's anyone know how to remove or change the host address from the terminal???

sphinx@***.***.***.***.***:~$

the host address that i covered up with stars.
in windows i could change this as the computer name but i dont know how to in ubuntu.
mines the address given by my isp and its quite long and annoying.
removing it would be best but i can live with just changing it.

thnx in advance

---

### Post by bodhi.zazen on 2006-10-05
Add a line in your ~/.bashrc:

```
gedit ~/.bashrc
```

Add this line:> # Comment in the above and uncomment this below for a color prompt

PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

Save and exit gedit.

Add this to /root/.bashrc:```
sudo gedit /root/.bashrc
```

> PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

Close (log-off) your terminal and re-start.

Additional options:

[custom prompts](http://www.linuxjournal.com/article/3215)

[Custom Prompt 2](http://www.freebsddiary.org/prompt.php)

---

### Post by uk_sphinx on 2006-10-05
errrrr yeahh thanks.

the first one gave me a blue squiggly line " ~ "  epreciate that

dont know what the second one did.

il read them links you gave me but i wanted to get rid of the bit that goes....

@cpc1.cust.123563.cable.ntlword.com

but thanks for the squiggly line. i always wanted one of those\\:D/

[edit] yikes, come to think of it, that was alot of code for 1 squiggle
BINGO got it 
thnx

---

### Post by bodhi.zazen on 2006-10-05
> **uk_sphinx said:**
> errrrr yeahh thanks.

the first one gave me a blue squiggly line " ~ "  epreciate that

dont know what the second one did.

il read them links you gave me but i wanted to get rid of the bit that goes....

@cpc1.cust.123563.cable.ntlword.com

but thanks for the squiggly line. i always wanted one of those\\:D/

[edit] yikes, come to think of it, that was alot of code for 1 squiggle
BINGO got it 
thnx

LOL :lol: So you are hapy now?

The second script will give you a red prompt if you change to root (sudo su). ;)

---

