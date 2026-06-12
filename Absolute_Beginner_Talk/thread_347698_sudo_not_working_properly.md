---
title: "sudo not working properly"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by no24 on 2007-01-27
i'm trying to change my trackpoint settings by using this command

```
sudo echo -n 187 > /sys/devices/platform/i8042/serio0/serio2/sensitivity 
```

it used to work just fine but now it says Bash: *** Permission denied (*** being the command)

I found that setting the terminal as root by using

<code>sudo -i</code>

will allow me to use the echo command just fine.

any idea how come it used to work and now it doesn't? it seems like sudo is only being applied to the first "echo" command and not the stuff written later in the line.

Thanks!

---

### Post by JamieC on 2007-01-27
Try this:
```

echo -n 187 > sudo /sys/devices/platform/i8042/serio0/serio2/sensitivity

```

---

### Post by taurus on 2007-01-27
```
sudo echo -n 187 > sudo /sys/devices/platform/i8042/serio0/serio2/sensitivity
```

---

### Post by no24 on 2007-01-27
it works, thanks.

is this the proper way to utilize the command? I guess I had typed it in differentbly before? i was certain that I had entered it without the second sudo command, because I copied the line into rc.local, and it was just 

```
echo -n 187 > /sys/devices/platform/i8042/serio0/serio2/sensitivity 
```

is it possible something changed?

---

### Post by JamieC on 2007-01-27
> **no24 said:**
> it works, thanks.

is this the proper way to utilize the command? I guess I had typed it in differentbly before? i was certain that I had entered it without the second sudo command, because I copied the line into rc.local, and it was just 

<code>echo -n 187 > /sys/devices/platform/i8042/serio0/serio2/sensitivity </code>

is it possible something changed?

The file permissions have not changed. If you're running as root, then sudo is not required. You do not need to be a super user to output (echo), but you do need to be a super user to write the files within /sys.

---

### Post by no24 on 2007-01-27
i see, thanks. I must have typed in a different series of commands when I first did it then. thanks.

---

