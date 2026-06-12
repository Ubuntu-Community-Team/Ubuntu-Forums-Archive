---
title: "conky programming language"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-24
Hello all,

I am currently running conky on my laptop and i an in the process of tweeking it to my liking.  The only problem is, is that i can search the internet for variables used in conky, but i am not familiar with the language used in conky and i do not understand the syntax.  I have a little bit of programming experience and i can look through a conky config file and halfway understand whats going on but i am never quite sure.

There are a few other things i would like to do with my .conkyrc file but i need to learn some basics about the programming language used.  

What language is used?

Does anyone know of any tutorials on the internet where i can teach myself how to write code for its particular language?

---

### Post by Rocket2DMn on 2007-07-24
I believe the .conkyrc file is just a configuration/data type file.  The conky program reads this then converts it to on screen display by accessing system variables and running terminal commands.  It's not a matter of learning the language, it's a matter of getting the syntax right.

---

### Post by ITdrummer on 2007-07-24
Well, how would one learn the syntax?

---

### Post by Rocket2DMn on 2007-07-24
Well, I'm not sure there is a whole lot to learn.
The static variables at the top simply declare how the program will function - you can look up what each of these do.  
Here is a list of dynamic variables (values that change while the program executes) - basically the output data that is monitored: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
You can use phrases like "$alignr" to tell everything after it on that line to align to the right, or ${color red} to make the rest of the line red, or just $color to have it return to the default color.  
Also, conky reads every space rather than just reading a bunch of spaces and tabs as "whitespace" like most configuration files are read as.  This means you can specify exactly how conky looks.
Fiddle around with it, try different config files, and you'll get the hang of it.

---

### Post by ITdrummer on 2007-07-24
for example, what significance does the dollar sign have?  Where do i put quotations? Brackets?  Line breaks? Slashes? just saying "play around with it" cannot be all there is to it.   Shouldn't there be a concrete syntax that the config file uses?  

Like, instead of (color red)  why couldnt i just put  [color: red]  ? 


Im sorry if im being difficult?

---

### Post by Rocket2DMn on 2007-07-24
You're not being difficult, these are good questions.  In many languages, esp. in non-compiled languages, there are characters that tell the reader that something is a variable, in many cases they use the $ sign.
You use ${color red} to note that the variable "color" is being changed to value "red", and when you just do $color or ${color}, you are reverting to the default color defined at the top of the file since you are not assigning it a value.
A line break will simply start a new line in the output on the conky window.
It even allows the output from a command line call: ${execi command_goes_here}
    "execi" is a variable and it's value is the command
square brackets and slashes don't seem to have any particular use in conky.
Here are those static variables i mentioned: [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)
PS: I will change my above post, conky uses {} instead of ().

---

