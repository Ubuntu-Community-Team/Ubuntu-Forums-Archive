---
title: "Messages with  command line"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Nath on 2006-11-10
Hey,
Now I know that to send a message through the command line to a user within the same network you use the talk function but I am not really sure how this works please help me PPL

suppose I want to send the text "hello" to a person who's IP is 192.168.0.10 and my ip address is 192.168.0.70 how does this actually work

please some one give me the correct syntax for this command

Thanks

---

### Post by meborc on 2006-11-10
i'm not sure, but i remember from somewhere, that you should use ```
talk userXX@compname
```
for talk function... if you are using the same computer (server) and are loged in with different usernames, then just use
```
talk userXX
```

i might be wrong... try google ;)

---

### Post by echo $USER on 2006-11-10
You can also mail the user on the domain w/...
> mail user@domain
then follow the directions to comlete the request.

---

### Post by digby on 2006-11-10
Also, if you are on the same system (e.g. ssh to same machine), I believe you can use the write command.```
write username message
```

---

