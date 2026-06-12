---
title: "customizing shell"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by harys on 2006-04-18
hi, ive issued this script to customize the colour of prompt in my xterm but i have an error while opening my xterm : 
bash: [: missing `]'
harys@harys:~$

here's an extract of the script that ive written in my .bashrc :
#customizing the xterm
if [ "`basename $SHELL`" = "bash"]
then
export PS1="\e[ 34m\] user> \e[ 0m"
fi

thanks for your help. harys

---

### Post by ComplexNumber on 2006-04-18
try this:



#customizing the xterm
if [ "`basename $SHELL`" = "bash"]
then
export PS1="\e[ 34m\] user> \e[ 0m**]**"
fi

---

### Post by jrib on 2006-04-18
you are missing a space before the last bracket in:
```
if [ "`basename $SHELL`" = "bash"]
```

It should be: ```
if [ "`basename $SHELL`" = "bash" ]
```

---

### Post by harys on 2006-04-18
hi, thanks for the reply but i have this error message when i open the xterm : 

[ 34m user> [ 0m]

thanks once more for your help. harys

---

### Post by jrib on 2006-04-18
yeah that's what my prompt looked like too when i tried what you set PS1 as... what are you trying to do?

---

### Post by harys on 2006-04-19
hi just paste this in your .bashrc file and it should work :
export PS1="\[\e[36;1m\]\u@\[\e[32;1m\]\H> \[\e[0m\]".

for more infomation on this topic you can visit this url  : [http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/) . harys

---

