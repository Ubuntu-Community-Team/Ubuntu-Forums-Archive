---
title: "Basic firewall settings?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by dupa on 2006-12-28
Hello.
If I installed on a Linux machine an apache server and i would like to allow just some IP to access the port 80 of my pc, which is the most easiest way to do it?

In few words, i need to block every incoming call on my host, and just allow few hosts to access my box on a specific port (i.e. port 80 tcp)

Can you suggest me any easy-to-use tool to do this?

Thanks.

---

### Post by deadgobby on 2006-12-28
Here is what I found on Ubie's wiki 
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=firewall&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=firewall&titlesearch=Titles)
Gobby

---

### Post by TheWizzard on 2006-12-28
> **deadgobby said:**
> Here is what I found on Ubie's wiki 
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=firewall&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=firewall&titlesearch=Titles)
Gobby

doesn't really answer the question, does it?

anyway, what you're looking for is firestarter. it is the easiest by far (i tried almost everything i could find) and it is in the repos. just: 
```
sudo aptitude install firestarter
```

---

### Post by dupa on 2006-12-29
I would like to handle to "firewall configuration" using a simple text configuration file.

Something like:


```

deny all
allow 80.67.87.* tcp 80

```

In few words this config tells that every incoming connection should be blocked, and the only allowed connections from outside are on the port tcp 80 from the class C network 80.67.87.*

I have seen that iptables can be used also as a firewall, but looking over internet, it seems that you can configure iptables just issuing commands and not using just a simple text configuration file.

Anyone know if there any simple way to configure a firewall in a "only console" system using a simple config file as above?

Thanks.

---

### Post by mcduck on 2006-12-29
If you want to make your own firewall with iptables it's usually done by writing the configuration commands in a text file to create a script that you can se to run on every boot. So it really is configured by editing that script file.. ;)

Also iptables is included in kernel so using it you arent' wasting any extra resources. Most of Linux firewalls are just front ends to iptables.

---

