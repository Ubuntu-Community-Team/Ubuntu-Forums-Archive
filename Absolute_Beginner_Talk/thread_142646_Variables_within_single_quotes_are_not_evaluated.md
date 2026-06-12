---
title: "Variables within single quotes are not evaluated?"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-10
$echo 'HOME variable has value $HOME'
HOME variable has value $HOME

$echo "HOME variable has value $HOME"
HOME variable has value /home/john

However, I notice that ~/.bashrc, I have lines that go

export LS_OPTIONS='--color=auto'

alias ls='ls $LS_OPTIONS'

and the ls does expand out correctly to ls --color=auto in the commandline. I thought the single quotes are suppose to keep the content literally? aka ls should expand out to be ls $LS_OPTIONS on the commandline?

Would alias ls="ls $LS_OPTIONS" be handled 'more' correctly?


Thanks !
*confused*

---

### Post by goatflyer on 2006-03-10
Correct, bash will not expand $ in single-quotes --- as documented.

What is happening is you are definiing an alias, and the single quotes are used when defining the alias, but when the alias is being used, the single quotes are no longer there, so THEN (at time of using the alias) the $ gets expanded.

This is probably the behaviour you want --- get a fresh expansion of the alias each time you use it, rather than expand once when you define it.

Have I confused you more?

---

