---
title: "Proxy Confusion"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-03-02
Sometimes I can get a website and sometimes I can't. I keep getting this:

Server not found
Firefox can't find the server at [www.google.com](www.google.com).

    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.



However, If I reload, I can often then get the site. This wasn't happening yesterday, So how do I go about checking this network connection? I also get a message saying firefox is running a proxy that is refusing connection.

---

### Post by chggr on 2007-03-02
What are your proxy settings for firefox?
Edit -> Preferences -> Advanced -> Network -> Settings.

If you are using Autodetect proxy, maybe you sould change to manual proxy configuration, supplying all the available information (proxy ip and port)

---

### Post by Aurora Borealis on 2007-03-02
It says "direct connection to the internet."

---

### Post by steve101101 on 2007-03-02
it seems that you cannot see your network or internet. did you configure samba if your going through a windows network?

---

### Post by Aurora Borealis on 2007-03-02
Well, that's the thing: sometimes I get the error message,, but then I reload the page and I'm fine. And then I get that message again with the next web site I try to visit, and I may have to reload twice or so and it behaves normally. I'm not sure what Samba is.

---

### Post by steve101101 on 2007-03-02
Samba is a program that allows your linux computer to "talk" to the windows network and its computers. Do you connect to a windows network and if so can you see the windows computers? If not follow the directions on my other thread here ..... 

[http://ubuntuforums.org/showthread.php?t=370892]("http://ubuntuforums.org/showthread.php?t=370892")

---

### Post by Aurora Borealis on 2007-03-02
I don't think I'm on a network. But I'm so green when it comes to computers-everything I know about them I learned pretty much this week. I've been trying to survive on gui for years and it just doesn't work anymore. I don't think I'm on a network, though.

---

### Post by Aurora Borealis on 2007-03-03
Thanks, everyone. (I did a reinstall and I'm not having problems anymore.)

---

