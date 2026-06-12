---
title: "spanish characters in latex"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Jawsman on 2007-12-05
Hi there... i'm trying to produce some Latex documents and I can't get to create the spanish caracters like

á é í ó ú ¿ ¡ and ñ

I'm using the packages

\usepackage[spanish]{babel}
\usepackage[latin1]{inputenc}

but nevertheless I don't get the expected output but other weird things... for example if I write:

> \begin{document}

Choripán

\end{document}

I get
> 
       &#771;
ChoripA¡n


I think it's due to Ubuntu encoding different for this special characters... can anyone help?
THANKS!

---

### Post by mali2297 on 2007-12-05
Try
```

Chorip\'an

```

Also,
```

!` ?` \~n

```

However, you should not have to use those commands.
Does the error occur already in the editor as you type the character, or after compilation?

Run in the terminal:
```

locale

```
What is the output?
Which editor do you use?

---

### Post by Jawsman on 2007-12-05
> LANG=es_AR.UTF-8
LC_CTYPE="es_AR.UTF-8"
LC_NUMERIC="es_AR.UTF-8"
LC_TIME="es_AR.UTF-8"
LC_COLLATE="es_AR.UTF-8"
LC_MONETARY="es_AR.UTF-8"
LC_MESSAGES="es_AR.UTF-8"
LC_PAPER="es_AR.UTF-8"
LC_NAME="es_AR.UTF-8"
LC_ADDRESS="es_AR.UTF-8"
LC_TELEPHONE="es_AR.UTF-8"
LC_MEASUREMENT="es_AR.UTF-8"
LC_IDENTIFICATION="es_AR.UTF-8"
LC_ALL=

is the locale output
when I write in the text editor I see the right characters :(
any idea?

pd: I know about those commands (!` ?` \~n) but i want to use the spanish package

---

### Post by willie_wang on 2007-12-05
> **Jawsman said:**
> spanish characters in latex

ooh la la! does nobody else see the funny side of this thread title? hehe!

---

### Post by Jawsman on 2007-12-05
I don't, but I don't manage English too deeply

I'm trying to alter the latin1.def file...
does anyone know how these work?:

> \DeclareInputText{166}{\textbrokenbar}
\DeclareInputText{168}{\"{}}
\DeclareInputText{180}{\@tabacckludge'{}}
\DeclareInputText{184}{\c\ }
\DeclareInputText{188}{\textonequarter}
\DeclareInputText{189}{\textonehalf}
\DeclareInputText{190}{\textthreequarters}
\DeclareInputText{160}{\nobreakspace}
\DeclareInputText{176}{\textdegree}
\DeclareInputText{161}{\textexclamdown}

---

### Post by mali2297 on 2007-12-05
Check that you have all relevant packages installed, like
texlive-lang-spanish
texlive-fonts-extra

Have you tried different editors (gedit,nano,emacs)?

---

### Post by Jawsman on 2007-12-05
I have tried all those editors... and nothing!
I have installed those packages... and nothing!

I am begining to suspect that when I type ñ for example, the machine writes other two characters... look at this:

INPUT:
> ñ\\
á\\
é\\
í\\
ó\\
ú\\
¡\\
¿\\

OUTPUT (errors in between)
>      &#771;
    A±
 &#771;
A!&#8216;
 &#771;
Ac
 &#771;
A
 &#771;
A3
 &#771;
Ao
&#710;
A!&#8216;
&#710;
A?&#8216;


does this say anything to you?

---

### Post by mali2297 on 2007-12-05
Have you tried this?
```

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}

```
instead of
```

\usepackage[latin1]{inputenc}

```

---

### Post by Jawsman on 2007-12-05
mali2297 I love you

that's it
 dunno where you got the data, but it worked!!!!!

I'm glad to be in this great community
THANKS!!!

ps:the graphic quality is lower now, but I don't really care

edit: is there any way of giving you reputation points or something?

---

### Post by mali2297 on 2007-12-05
> **Jawsman said:**
> 
dunno where you got the data,

I got the advice from some support page concerning swedish characters. It is strange though, latin1 works fine for me in ubuntu.

> 
ps:the graphic quality is lower now, but I don't really care


Perhaps you don't have to use the second line (fontenc).

> 
edit: is there any way of giving you reputation points or something?

No need, the beans are my reward. I hope to get a coffee cup soon. :-)

---

