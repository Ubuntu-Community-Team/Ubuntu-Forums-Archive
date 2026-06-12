---
title: "Wireless help guide"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by htx on 2005-12-03
Ok I know a lot of people have trouble installing wireless cards with linux and I was one of them.  After doing a lot of research I came up with a way to get my wireless card to work flaulessly.  I use a linksys wmp54g pci card, and I know this also works the wmp54g usb adapter.  You can try anyother card with this method and see if it works, and if it does work please post the model of the card in this thread.  

Ok First what you need to do is copy two files from the windows drivers.  I took the .inf file and the .sys file 

Now I put these two files in a new folder called drivers all in my home folder.  You can put them anywhere I just like to keep things somewhat organized.

Ok now that you have the drivers you need to install ndiswrapper.  All you need to do is go into synaptic package manager, search for ndiswrapper then check it and install it.  Or you can do in the terminal:
```
sudo apt-get install ndiswrapper
```

Ok now ndiswrapper is installed so now we can install the wireless card.

Now what you want to do is get into the folder drivers were the drivers are located, to do this I would log in as ```
su (then it will ask for your password)
``` 

Now to get into the folder we will use the cd command

```
cd /home/yourusername/drivers
```

Now you are in the folder you need to be.

Ok now you can do:
```
ndiswrapper -i yourdriver.inf
```

Now if you type the driver ndiswrapper will say the driver isn't installed right but it will still list the driver to remove the driver type:
```
ndiswrapper -e yourdriver (.inf is not needed unless you spelt .inf wrong)
```

Now to show what drivers are install type:
```
ndiswrapper -l
```

Now you will make a config file.

Type:
```
ndiswrapper -m
```

Ok now let's start it up:
```
modprobe ndiswrapper
```

Now type:
```
dmesg
```

Ok now it gets easier because the rest we can use the gui in gnome.

Go to System, Administration, Networking.

Now you should see the wireless card in there but it is not enabled yet.  To do this first right click on the card and go to properties, and you want to enable this connection.  Now you can either set it as a static IP or use DCHP to do it for you, I used DHCP.
[IMG]http://www.netfxpro.com/~lou/1.png[/IMG]
[IMG]http://www.netfxpro.com/~lou/2.png[/IMG]

Now you want to Activate the connection.  Now test out the internet and see if it works.

One last thing to keep it running everytime you restart the computer:
```
echo "Set up wireless lan"
Modprobe ndiswrapper
dhcpcd wlan0
``` Remember to replace the 0 with whatever your connection says it is.

Now you should be done good luck!  Please feel free to add to this!

Ok

---

