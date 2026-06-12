---
title: "BASH commands..."
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Greggle on 2007-06-10
I'm trying to learn said commands, but have hit a wall with a seemingly simple operation.

*cd Desktop | rm -r test*

Why won't this work?

Error: "Cannot remove 'test': No such file or directory."

Note: I am trying to run this command from 'my'(greg, in this case) directory within 'home' or, more simply, the default directory that is displayed upon opening the terminal.

'test' is a text file I have saved on my desktop.

I really just want to navigate to a certain directory and remove a file within it. I don't care how it's accomplished.

-Thanks, gang...

---

### Post by odiseo77 on 2007-06-10
Maybe ***cd Desktop && rm test*** should work??

If you want to get familiarized with the terminal and all its fabulous tricks, I'd suggest you to read [http://www.linuxcommand.org/](http://www.linuxcommand.org/) It's a very useful resource

Regards.

EDIT: The command you're trying to execute (cd Desktop | rm -r test) doesn't work because the pipe sign (|) does the job of passing the output of the first command you introduce to the second command (it's useful to pass text outputs to other commands; for example to pass text output of a certain command to the grep command in order to find a certain string). The logical 'and' (**&&**) allows you to execute one command *and* a second one after the first one.

---

### Post by Greggle on 2007-06-10
Eureka! Thanks, odiseo'!

You know, that's neat how the pipe(the character) *passes* the output of the first to the second.

Even considering my 'extensive'(I'm definitely over-dramatizing here) in programming I wouldn't have guessed it would have done that.

In retrospect(again, with my 'extensive' programming), the logical and makes more sense.

Again, thanks!

P.S. Thanks for the link.

---

