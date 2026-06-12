---
title: "installing dictionaries"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-26
i want english dictionary almost exactly the same like babylon for windows with 
ctrl +rigth mouse click on a word gives meaning of that.

is there any dictionary for ubuntu either from apt-get or by downloading and installing manually.

if it is in apt-get plz write commands to install it.if a dictionary with somewhat like above shortcut is not available no matter.i need source of finding meanigs to english in english i.e english to english dictionary.if multiple are available in ubuntu apt plz tell about them also  and their commands.

is there any way to look or search a particular software in apt-get?
thnx in advance

---

### Post by joshrobinson on 2006-05-26
[QUOTE=u04f061]i want english dictionary almost exactly the same like babylon for windows with 
ctrl +rigth mouse click on a word gives meaning of that.

is there any dictionary for ubuntu either from apt-get or by downloading and installing manually.

if it is in apt-get plz write commands to install it.if a dictionary with somewhat like above shortcut is not available no matter.i need source of finding meanigs to english in english i.e english to english dictionary.if multiple are available in ubuntu apt plz tell about them also  and their commands.

is there any way to look or search a particular software in apt-get?
thnx in advance[/QUOTE]

should be one in applications >accessories >dictionary

if not click applications, add remove programs, then look for it

---

### Post by Ptero-4 on 2006-05-26
The command for apt is sudo apt-get install <program name>.
Where <program name> is the name of the app you want to install, and the password it asks is the one for the account you created when you installed ubuntu.

---

### Post by u04f061 on 2006-05-26
[QUOTE=joshrobinson]should be one in applications >accessories >dictionary

if not click applications, add remove programs, then look for it[/QUOTE]

this dictionary is as slow as tortoise.i swear i wrote a word on it and it took 15 minute without any search after that it was not responding and i forced it to quit

i think u hav'nt understood what i said in my post.

i have no dictionary in ubuntu.my pc is dual boot.i want to install a dictionary.i spent 30 minutes on google and found all applications for windows.

---

### Post by joshrobinson on 2006-05-26
[QUOTE=u04f061]this dictionary is as slow as tortoise.i swear i wrote a word on it and it took 15 minute without any search after that it was not responding and i forced it to quit

i think u hav'nt understood what i said in my post.

i have no dictionary in ubuntu.my pc is dual boot.i want to install a dictionary.i spent 30 minutes on google and found all applications for windows.[/QUOTE]

i understood your post, i didnt know that you tried that one already and it didnt work for you..not sure why its slow for you, its instant every word i tried

it connects to the internet for the definitions. are you on dialup?

---

### Post by u04f061 on 2006-05-26
[QUOTE=joshrobinson]i understood your post, i didnt know that you tried that one already and it didnt work for you..not sure why its slow for you, its instant every word i tried

it connects to the internet for the definitions. are you on dialup?[/QUOTE]

no,i use 100Mb/s lan cable.

is'nt there any offline dictionary?

---

### Post by nanotube on 2006-05-26
[QUOTE=u04f061]no,i use 100Mb/s lan cable.

is'nt there any offline dictionary?[/QUOTE]
if you want an offline dictionary, install package "wordnet"
it's pretty good.
to run it in commandline mode, use command 'wn', to run in gui mode, use command "wnb"
(you can create a shortcut to wnb in your menu for convenience).

---

### Post by PriceChild on 2006-05-26
[quote=u04f061]no,i use 100Mb/s lan cable.[/quote]

No... that's the speed you are connected to another computer near you.

What is the speed of the internet where you use ubuntu? If its dialup, then that'll probably be why its so slow.

---

### Post by ifokkema on 2006-05-26
[QUOTE=PriceChild]What is the speed of the internet where you use ubuntu? If its dialup, then that'll probably be why its so slow.[/QUOTE]

A firewall blocking the port may also cause it to 'hang'....

---

### Post by u04f061 on 2006-05-26
[QUOTE=PriceChild]No... that's the speed you are connected to another computer near you.

What is the speed of the internet where you use ubuntu? If its dialup, then that'll probably be why its so slow.[/QUOTE]

ok,in windows when i download something using intenet download manager ,the average speed it downloads is 20kb/s

---

### Post by u04f061 on 2006-05-27
[QUOTE=nanotube]if you want an offline dictionary, install package "wordnet"
it's pretty good.
to run it in commandline mode, use command 'wn', to run in gui mode, use command "wnb"
(you can create a shortcut to wnb in your menu for convenience).[/QUOTE]

how to use wordnet in command line.ie if i want to search utopia, i used following

ejaz@ejaz:~$ wn utopia

Information available for noun utopia
        -antsn          Antonyms
        -hypen          Hypernyms
        -hypon, -treen  Hyponyms & Hyponym Tree
        -synsn          Synonyms (ordered by estimated frequency)
        -famln          Familiarity & Polysemy Count
        -coorn          Coordinate Terms (sisters)
        -hmern          Hierarchical Meronyms
        -grepn          List of Compound Words
        -over           Overview of Senses

No information available for verb utopia

No information available for adj utopia

No information available for adv utopia
ejaz@ejaz:~$

however graphical command wnb works

---

### Post by vladozan on 2006-05-27
I am using wine to run a wrodweb dictionary and it works perfectly.

How about the multi-lingual dictionaries? I am looking for some Slovak-English dictionary. Is there some linux native one i can use?

---

### Post by u04f061 on 2006-05-27
[QUOTE=vladozan]I am using wine to run a wrodweb dictionary and it works perfectly.

How about the multi-lingual dictionaries? I am looking for some Slovak-English dictionary. Is there some linux native one i can use?[/QUOTE]

if u can use wordweb using wine then u may be able to use babylon which multingual also

---

### Post by vladozan on 2006-05-27
[QUOTE=u04f061]if u can use wordweb using wine then u may be able to use babylon which multingual also[/QUOTE]

unfortunately i can't run babylon, becasue of msxhtml 3.0 (although i have installed 4.0 SP). Anyway is there something free and still linux native?

---

### Post by patrick295767 on 2006-05-27
[QUOTE=vladozan]I am using wine to run a wrodweb dictionary and it works perfectly.

How about the multi-lingual dictionaries? I am looking for some Slovak-English dictionary. Is there some linux native one i can use?[/QUOTE]
  
I am using kydpdict & ydpdict (polish, it's kind of  the same language (almost) , (prawie) tak tak ?)
  
To install this polish-english dict. myscriptkydpdictanddico.sh: 
(lucky !!)
(lower case the data filenames !!! :KS)
```
#!/bin/bash
mkdir /root/miniram
## dictionaruies
# ydpdict
apt-get -f -y install kdict
apt-get -f -y install ydpdict 
apt-get -f -y install konsole
apt-get -f -y install luit
apt-get -f -y install gdict
apt-get -f -y install gnome-dictionary
#
apt-get -f -y install kydpdict
apt-get -f -y install gdict
apt-get -f -y install 
## since kydpdict is not in the repos...
##let's make it work
export QTDIR=/usr/share/qt3
export QTDIR=/usr/share/qt3
##cd /root
##wget http://membres.lycos.fr/patrick295767/miniram/packages/kydpdict-0.9.2.tar.bz2
cd /root/miniram
wget http://patrick295767.sitesled.com/miniram/kydpdict-0.9.2.tar.bz2
tar -xjf kydpdict-0.9.2.tar.bz2
cd kydpdict-0.9.2
./configure
make
make install
cd /root/miniram
#wget http://membres.lycos.fr/patrick295767/miniram/packages/ydpdict.conf
wget http://patrick295767.sitesled.com/miniram/ydpdict.conf
cp ydpdict.conf /etc/ydpdict.conf
## done man !!
cd /root/miniram


```
  
To run my script: 
```
sudo bash
chmod +x myscriptkydpdictanddico.sh
sh myscriptkydpdictanddico.sh
```
  
Enjoy !!
  
Let me know if you'd need more nfo !! Papa i na razie !

---

### Post by u04f061 on 2006-05-27
can any body tell me how to search a word in wordnet by command line ,instead of opening it graphically.
i mean if i want to search for mississipy what should i type?

---

### Post by nanotube on 2006-05-28
[QUOTE=u04f061]how to use wordnet in command line.ie if i want to search utopia, i used following

ejaz@ejaz:~$ wn utopia

Information available for noun utopia
        -antsn          Antonyms
        -hypen          Hypernyms
        -hypon, -treen  Hyponyms & Hyponym Tree
        -synsn          Synonyms (ordered by estimated frequency)
        -famln          Familiarity & Polysemy Count
        -coorn          Coordinate Terms (sisters)
        -hmern          Hierarchical Meronyms
        -grepn          List of Compound Words
        -over           Overview of Senses

No information available for verb utopia

No information available for adj utopia

No information available for adv utopia
ejaz@ejaz:~$

however graphical command wnb works[/QUOTE]
well, clearly the commandline command also works - it is telling you that information is available for noun utopia.
so now, if you want the overview of senses, issue command
```
wn utopia -over
```
and you can of course also try other stuff from the list of available information it gave you. :)

---

### Post by ifokkema on 2006-05-28
[QUOTE=u04f061]can any body tell me how to search a word in wordnet by command line ,instead of opening it graphically.
i mean if i want to search for mississipy what should i type?[/QUOTE]

Try
```
man wn
```

---

### Post by vladozan on 2006-05-28
Thank you for the script. i tried it, and all went well untill it couln't connect the sever

[http://membres.lycos.fr/patrick295767/miniram/packages/kydpdict-0.9.2](http://membres.lycos.fr/patrick295767/miniram/packages/kydpdict-0.9.2).

  
Anyway i installed the stardict and if nothing i am quite content with it, on the other hand i am never content enough to stop search for better options

---

### Post by u04f061 on 2006-05-29
[QUOTE=vladozan]Thank you for the script. i tried it, and all went well untill it couln't connect the sever

[http://membres.lycos.fr/patrick295767/miniram/packages/kydpdict-0.9.2](http://membres.lycos.fr/patrick295767/miniram/packages/kydpdict-0.9.2).

  
Anyway i installed the stardict and if nothing i am quite content with it, on the other hand i am never content enough to stop search for better options[/QUOTE]

i also installed this dict but it says that download some dictionaty from its site.i did this and downloaded 80Mb dict.in site he had written that extract it in usr/share
i did this ,still stardict is not working.plz tell me how to install that 80Mb dict so that star dict can recognize it

---

### Post by vladozan on 2006-05-29
[QUOTE=u04f061]i also installed this dict but it says that download some dictionaty from its site.i did this and downloaded 80Mb dict.in site he had written that extract it in usr/share
i did this ,still stardict is not working.plz tell me how to install that 80Mb dict so that star dict can recognize it[/QUOTE]

I could not even find the dictionary to download. You have to have the stardict format dictionary, otherwise stardict does not recognize it.

---

### Post by u04f061 on 2006-05-29
what do umean dear. u are not using it.

---

### Post by vladozan on 2006-05-30
[QUOTE=u04f061]what do umean dear. u are not using it.[/QUOTE]

I'm not using the dictionary from that link. I did install stardict from repositories

> sudo apt-get install stardict

Then downloaded dictionaries from [http://stardict.sourceforge.net](http://stardict.sourceforge.net) and exracted them into /usr/share/stardict/dict directory. 

That was all. I don't know what 80 Mb file you meant. Probably that with sounds, but i haven't downloaded and installed it yet, but i might do it when i will have more time.

---

### Post by patrick295767 on 2006-06-07
[QUOTE=u04f061]can any body tell me how to search a word in wordnet by command line ,instead of opening it graphically.
i mean if i want to search for mississipy what should i type?[/QUOTE]

Even better:
type 

```
sudo apt-get -f -y install festival
wn utopia -over 
wn utopia -over | festival --tts
```

You like ?

---

### Post by patrick295767 on 2006-06-07
[QUOTE=vladozan]Thank you for the script. i tried it, and all went well untill it couln't connect the sever

[http://membres.lycos.fr/patrick295767/miniram/packages/kydpdict-0.9.2](http://membres.lycos.fr/patrick295767/miniram/packages/kydpdict-0.9.2).

  
Anyway i installed the stardict and if nothing i am quite content with it, on the other hand i am never content enough to stop search for better options[/QUOTE]
 
Sometimes (few hours) the server is down. Now, it's back again !! :KS :-)

---

### Post by nanotube on 2006-06-07
[QUOTE=patrick295767]Even better:
type 

```
sudo apt-get -f -y install festival
wn utopia -over 
wn utopia -over | festival --tts
```

You like ?[/QUOTE]
hehe, cute! :)

---

### Post by ropers on 2006-10-11
You are digging in the wrong place, but [your enlightenment awaits]("http://www.ubuntuforums.org/showthread.php?p=1605082").

---

### Post by medya on 2007-04-27
you can use StarDict and you can import babylon dictionaries... read [more here]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

---

