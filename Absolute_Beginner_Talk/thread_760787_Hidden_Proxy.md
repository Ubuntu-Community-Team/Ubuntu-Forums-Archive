---
title: "Hidden Proxy?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Marcel Proust on 2008-04-20
I'm using GG, and I recently tried to install Tor. After the system crashed, no traces of that installation seemed to be left, but when I try to use the update manager or synaptic I get a message saying  
[I]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...dy/Release.gpg](http://archive.ubuntu.com/ubuntu/dis...dy/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)[/I]

I'm rather new to Linux, and it would be great if someone could point me in the right direction...

---

### Post by quirks on 2008-04-20
I don't know what an installation of Tor all does in the background. Probably it messed up with your proxy configuration. You should have a look at the settings in System -> Administration -> Network Proxy.

Also, you can check in Synaptic, if the settings are correct under Settings -> Preferences -> Network tab. 

In addition, check if the http_proxy and ftp_proxy environment variables are set; open a terminal and type:
```
echo $http_proxy
echo $ftp_proxy
```

---

### Post by Marcel Proust on 2008-04-22
> **quirks said:**
> I don't know what an installation of Tor all does in the background. Probably it messed up with your proxy configuration. You should have a look at the settings in System -> Administration -> Network Proxy.

Also, you can check in Synaptic, if the settings are correct under Settings -> Preferences -> Network tab. 

In both cases, it says something like 'direct connection to the internet' (message translated by yours truly).

> **quirks said:**
> In addition, check if the http_proxy and ftp_proxy environment variables are set; open a terminal and type:
```
echo $http_proxy
echo $ftp_proxy
```

I get 
[http://localhost:4001](http://localhost:4001)

and 

(i.e. nothing at all).

---

### Post by quirks on 2008-04-22
Delete the http_proxy environment variable. I have found out that it is used by Synaptic. I cannot understand, however, how or why. Someone needs to explain this to me ...

You can remove the variable with this command:
```
unset http_proxy
```
Now, test if you can connect to the Internet again with Synaptic. Open it and click the Reload button. It should not return any errors.

To make the change permanent, we have to find out where this variable is set. I suppose this is done in ~/.bash_profile or ~/.bashrc. Open the files in your favorite text editor:
```
gedit ~/.bashrc
gedit ~/.bash_profile
```
And remove any lines in these files that look similar to this:
```
export http_proxy="http://localhost:4001"
```

If you have any trouble following the above steps, let me know.

---

### Post by spiderbatdad on 2008-04-22
```
sudo apt-get purge anon-proxy
```

---

### Post by Marcel Proust on 2008-04-25
Thank you very much. 

@* quirks*:

After running 

```
unset http_proxy
```

the command 
```
echo $http_proxy
```

returned an empty line, so something did happen. However, I still get the same error message when running synaptic. 
The variable is not in either ~/.bash_profile or ~/.bashrc.

@*spiderbatdad*:

After running

```
sudo apt-get purge anon-proxy
```

I get a message telling me that anon-proxy is not installed and will therefore not be removed.

---

### Post by quirks on 2008-04-25
1. Can you tell me the exact name of the package, which you tried to install? Is it **anon-proxy**? I could have a look at the contents of that package and see, how it configures your system, so we can undo the changes.

2. After you unset the **http_proxy** environment variable, how did you start Synaptic? Did you go to System -> Administration -> Synaptic Package Manager? Or did you type **gksu synaptic** in the same terminal  where you unset the variable? You should try starting it from the terminal, because I found hints on the Internet that processes inherit the environment variables of their parent process. If you start Synaptic through the menu, it inherits the variables from Gnome (where **http_proxy** is still set) and not from the terminal. You can reproduce this "phenomenon" by opening two terminals and unsetting the variable in one of them. In the other terminal, the variable should still be set.

3. Do you have the file **.gnomerc** in your home directory? Maybe the environment variable is set there.

---

