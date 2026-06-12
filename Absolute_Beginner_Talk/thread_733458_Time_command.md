---
title: "Time command"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by leetcharmer on 2008-03-23
I want to find out the time it takes to compress a tar archive.  I found the 'time' command is sufficient for my needs, but I want the output to go to a file.  I thought this would work according to the man pages:

```
time --output=log [command]
```

but it comes back saying that --output is not a proper command.  Is that not the correct parameter?  Thanks.

---

### Post by LaRoza on 2008-03-23
You can dump the output of commands into a file with a '>'

```

ls > filelist.text

```

Nothing will be on screen, but the output of that command will be in a file called "filelist.text".

---

### Post by nick_h on 2008-03-23
The problem seems to be with the shell.  Try:
```
dash -c 'time --output=log ls'
```
Using bash rather than dash causes the errors.

Redirecting the output as suggested by LaRoza doesn't work either.  I tried using 2> since time outputs to stderr rather than stdout.  The reason for this is that the redirection will be that of the command (ls in my example) not the time command.

---

### Post by leetcharmer on 2008-03-23
> **nick_h said:**
> The problem seems to be with the shell.  Try:
```
dash -c 'time --output=log ls'
```
That worked!! Do you know why it's a problem with the shell?

---

### Post by nick_h on 2008-03-24
> Do you know why it's a problem with the shell?
No, I don't know why.  It seems to ignore the options completely.

I can't find a bug reported on launchpad.

---

### Post by leetcharmer on 2008-03-26
I have a script that executes the time command within in, and at the beginning I create two variables:
host=$1
vm=$2

when I call these variables within my dash -c 'time ...' command, the variables return no value.  How can I bring the data of these variables within my time command?

Thanks

---

### Post by nick_h on 2008-03-26
Either include the variables in your command:
```
dash -c 'test=somevalue; echo $test'
```
or export the variables:
```
export test=somevalue
dash -c 'echo $test'
```

---

