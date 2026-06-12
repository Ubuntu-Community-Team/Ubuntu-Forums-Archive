---
title: "Help with simple script"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by 3ntity on 2006-02-19
Hello,
I would like to know how to 'answer a terminal's question/request' for input through a script. Take the su command, after i type it, it asks for a password. How can i write a script that fills in the password (i.e. 'answers' the terminal)? The following does not work (though i didn't expect it to :P):
     su
     <password>

The su thing was just an example though, this is for more general use,
Thanks

---

### Post by Gimbo on 2006-02-19
I've very little idea how you would get scripts to "answer" the terminal, or even if it's possible. What I do know is that it has potential security implications. There's a reason you're asked for your password, and that is that it means all important system changes have to be approved first. Logging in as root or somehow giving yourself permanent root priveleges would have the same effect as auto-filling the password field. I'm sure someone will be able to tell you how to do one of these, but I wouldn't recommend it for the reasons stated above.

For more "general" use, I would guess that you would need to modify the script you're running so that the required information was built in, but I don't really know.

---

### Post by cwaldbieser on 2006-02-19
[QUOTE=3ntity]Hello,
I would like to know how to 'answer a terminal's question/request' for input through a script. Take the su command, after i type it, it asks for a password. How can i write a script that fills in the password (i.e. 'answers' the terminal)? The following does not work (though i didn't expect it to :P):
     su
     <password>

The su thing was just an example though, this is for more general use,
Thanks[/QUOTE]
The su example is somewhat peculiar, however, if you want to have pre-determined responses to most CLI programs that request information, you just put the responses in a text file and redirect the standard input of your command to come from that file.  For example:
```

$ tac < my_input.txt

```
The "tac" command reads from standard input and writes the results to standard output.  It is a pretty simple example, but there are not a lot of interactive commands that come to my mind at the moment.

su, sudo, and commands that ask for a password are usually an exception to this rule, because they try very hard to make sure their input is coming from a console.  You might need to use a program like "expect" in order to talk to programs like that.

---

