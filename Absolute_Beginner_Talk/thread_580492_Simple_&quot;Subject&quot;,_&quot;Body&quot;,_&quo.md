---
title: "Simple &quot;Subject&quot;, &quot;Body&quot;, &quot;Recipient&quot; command line e-mailer?!"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-18
I need a simple, but actually functional command for sending a mail to <person> with the subject <subject> and the body of text <body>.  There must be a way to do this!?!  "Mail" doesn't seem to comprehend the concept of "body" :p...

---

### Post by llamakc on 2007-10-18
echo "asdf" | mail -s "subject" recipient

---

### Post by ryanVickers on 2007-10-18
doesn't seem to work...

---

### Post by llamakc on 2007-10-18
sudo apt-get install mailx

---

### Post by ryanVickers on 2007-10-18
no, I *_do_ have* it installed... ;)

---

### Post by llamakc on 2007-10-18
echo "asdf" | mail -s "your subjectline" name-of-recipient

like

```


echo "blah blah" | mail -s "blah email" ryan


```

Cut and paste that but use YOUR username at the end of the line. That character between blah" and mail is the PIPE, which is the shifted character on the backslash (usually). Try cut-pasting. You can substitute "ryan" with "ryan@hotmail.com" or whatever.

---

### Post by llamakc on 2007-10-18
Additionally you can have a flat-file like "mybody.txt" that you pipe to mail like this:

```

cat /path/to/mybody.txt | mail -s "my subject" ryan@hotmail.com


```

---

### Post by ryanVickers on 2007-10-18
both didn't work! ](*,)

---

### Post by llamakc on 2007-10-18
This isn't the same computer with permission issues, is it?

Those commands work fine for me on my machine, and those commands have worked fine for me for 10 years.

---

### Post by ryanVickers on 2007-10-18
well, yeah ;)

Does it need to be sent *from* someone to work, or, yeah, what will it put in the "from" category?

---

### Post by llamakc on 2007-10-18
It will come from the username that it is being passed into the shell by.

Are you entering this stuff in a terminal?

---

### Post by ryanVickers on 2007-10-18
OK then, it should work fine :p

It's a (bash) shell script, but yeah, it's in the terminal ;)

---

### Post by llamakc on 2007-10-18
> **ryanVickers said:**
> OK then, it should work fine :p

It's a (bash) shell script, but yeah, it's in the terminal ;)

Don't you think that you should post the contents of your script then? Most likely the error is in there.

---

### Post by ryanVickers on 2007-10-18
well, I know it';s fine because it works up to the point where it has to send the mail, and then doesn't send it, and also I tried the commands by themselves out of the script and it still didn't work :p, but 

```

#!/bin/bash
while [ 1 == 1 ]; do
rm "$HOME/tempIP.dat" >/dev/null 2>&1
ifconfig>>"$HOME/tempIP.dat"
cat "$HOME/tempIP.dat" | mail -s "my subject" 'ryan.externaldrive2@gmail.com'
rm "$HOME/tempIP.dat" >/dev/null 2>&1
sleep 1800
done

```

I've tried the mail parameters with and without different kinds of quotes in different places as well - no change...

---

### Post by ryanVickers on 2007-10-18
[B]WAIT!!!
[/B];)

I just got like 500 emails from "Ken Clark" with what I wanted :p  Oh dear, could it be any slower... ](*,)

---

### Post by llamakc on 2007-10-18
> **ryanVickers said:**
> well, I know it';s fine because it works up to the point where it has to send the mail, and then doesn't send it, and also I tried the commands by themselves out of the script and it still didn't work :p, but 

```

#!/bin/bash
while [ 1 == 1 ]; do
rm "$HOME/tempIP.dat" >/dev/null 2>&1
ifconfig>>"$HOME/tempIP.dat"
cat "$HOME/tempIP.dat" | mail -s "my subject" 'ryan.externaldrive2@gmail.com'
rm "$HOME/tempIP.dat" >/dev/null 2>&1
sleep 1800
done

```I've tried the mail parameters with and without different kinds of quotes in different places as well - no change...

What's wrong with

```

#!/bin/bash
ifconfig > "$HOME/tempIP.dat"
cat "$HOME/tempIP.dat" | mail -s "my subject" ken
rm "$HOME/tempIP.dat" >/dev/null 2>&1

```

Because you're using the > operand above, you are over-writing the file, and don't need to bother with removing it by deletion.

The above works for me. I think I just sent you a few emails.

---

### Post by ryanVickers on 2007-10-18
yeah, you sent about , hmm, ~64 * ~23... :p

---

### Post by llamakc on 2007-10-18
> **ryanVickers said:**
> yeah, you sent about , hmm, ~64 * ~23... :p

Your script is messed up. I ran your script.

---

### Post by ryanVickers on 2007-10-18
#!/bin/bash
while [ 1 == 1 ]; do
rm "$HOME/tempIP.dat" >/dev/null 2>&1
ifconfig>>"$HOME/tempIP.dat"
cat "$HOME/tempIP.dat" | mail -s "my subject" 'ryan.externaldrive2@gmail.com'
rm "$HOME/tempIP.dat" >/dev/null 2>&1
sleep 1800
done

it should send one, wait 30 minutes, and then repeat - very strange... still doesn't work for me - I'll try again with gutsy ;)...

---

### Post by llamakc on 2007-10-18
> **ryanVickers said:**
> #!/bin/bash
while [ 1 == 1 ]; do
rm "$HOME/tempIP.dat" >/dev/null 2>&1
ifconfig>>"$HOME/tempIP.dat"
cat "$HOME/tempIP.dat" | mail -s "my subject" 'ryan.externaldrive2@gmail.com'
rm "$HOME/tempIP.dat" >/dev/null 2>&1
sleep 1800
done

it should send one, wait 30 minutes, and then repeat - very strange... still doesn't work for me - I'll try again with gutsy ;)...

It's the syntax of your script, not the O/S.

---

### Post by ryanVickers on 2007-10-19
whatever the problem with the script is, I know the commands work because you tested it, and so I think that my installation of the command is messed up somehow - I'll try this again on the weekend when I have gutsy ;)

---

