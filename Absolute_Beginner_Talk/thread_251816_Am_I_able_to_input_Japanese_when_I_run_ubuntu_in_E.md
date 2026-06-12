---
title: "Am I able to input Japanese when I run ubuntu in English?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by harerama on 2006-09-05
Can anyone help me? I would prefer to run ubuntu in English however when I do it I CAN NOT  
 input Japanese into any application. Of course when I run ubuntu in Japanese I CAN with ctrl+space key. 

Am I able or not? That&s a question.

Thank you very much.

---

### Post by basilwatson on 2006-09-06
I had the same problem , I could  get it to type in katakana , but I couldnt get it to write Kanji ..

I read somewhere it had to be compiled , so I gave up ... 

I also would like to resolve this 

Stephen

---

### Post by seshomaru samma on 2006-09-06
You have to install SCIM
read [this]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake")

notice you need to install the im-switch for SCIM to work in an englsh session

---

### Post by basilwatson on 2006-09-06
following the instructions given in the link 

I get to here 
root@s-laptop:/home/s# gedit home/s/.scim/global

and command not found. the file .scim is there .....

Stephen

---

### Post by seshomaru samma on 2006-09-06
the im switch didn't wotk?
try to restart X (ctrl+alt+backspace) and then when you login run firefox or texteditor or something and use ctrl+space to start SCIM

---

### Post by basilwatson on 2006-09-06
not happening 

I have installed extra fonts , japanese , japanese big ,, by apt-get install japanese 

These istalled ok , but I just cant get it to swap languages 

I had a look at chinese in the wiki , but it called for a file download ..wget ... and iam not sure which one 

up to that I was ok ...

sudo apt-get install scim
sudo apt-get install scim-chinese   ( changed this to japanese) 
sudo apt-get install scim-config-socket
sudo apt-get install scim-gtk2-immodule
sudo apt-get install scim-tables-zh
wget -c [http://easylinux.info/uploads/fireflysung-1.3.0.tar.gz](http://easylinux.info/uploads/fireflysung-1.3.0.tar.gz)
sudo tar zxvf fireflysung-1.3.0.tar.gz -C /usr/share/fonts/truetype/
sudo chown -R root:root /usr/share/fonts/truetype/fireflysung-1.3.0/ 
sudo fc-cache -f -v

    * System -> Preferences -> SCIM Input Method Setup
    * To activate SCIM 

Press 'Ctrl + Space'


and still no Joy ...

If I could nail this ,,I could be rid of window , for ever ...yaaahooo 

Stephen

---

### Post by seshomaru samma on 2006-09-06
which wiki are you following?
I have installed Ubuntu and Xubuntu on many different kinds of machines and the link I provided in my first post always works. 
You really need only one command
```
im-switch -z “your locale” -s scim
```
this always works for me - Chinese/Japanese in an English session on X/K/ubuntu

---

### Post by harerama on 2006-09-06
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)
I did everything on this page and still doesn't work. When I use text editor 
then I right click "input method" comes out and I can input anything I like "kanji katakana hiragana". However not with Firefox nor with Openoffice.

when I command "im-switch -z jp_JP -s scim" it seems it doesn't do anything.

However it works great with Text Editor. But only text editor. There must be a way though after all I've started linux only a couple days ago.

---

### Post by harerama on 2006-09-06
Post Script,

Also when I command

gedit ~/.scim/global

This comes out

/DefaultKeyboardLayout = Japanese
/DisabledIMEngineFactories =
/SupportedUnicodeLocales = en_US.UTF-8,ja_JP.UTF-8

---

### Post by seshomaru samma on 2006-09-06
> **harerama said:**
> Post Script,

Also when I command

gedit ~/.scim/global

This comes out

/DefaultKeyboardLayout = Japanese
/DisabledIMEngineFactories =
/SupportedUnicodeLocales = en_US.UTF-8,ja_JP.UTF-8


I think the command should be 

```
im-switch -z en_US -s scim
```
because the im-switch is intended for non CJK&#12288;sessions
did you try login out and in?

---

### Post by harerama on 2006-09-06
&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#12290;&#12288;Thank you very very much. As you can see now I am able to input Japanese beautifully. It seems to work on everything. Firefox,Thunderbird,Openoffice. &#24863;&#35613;&#12391;&#12377;&#12290;

Everything work after I simply followed this.

think the command should be

Code:

im-switch -z en_US -s scim

because the im-switch is intended for non CJK&#12288;sessions
did you try login out and in?

again &#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#12290;

---

### Post by basilwatson on 2006-09-06
Well then what am I doing wrong??

I get to here

 Then you'll be ready to use im-switch (see just above). In Xubuntu, you will also have to apply the following instructions :
In case all of this doesn't work

You might have to add your locale as a supported locale, by editing (you might have to create it) the file ~/.scim/global (the ~ means it's in your home directory, the . that .scim directory is a hidden file. Just type in a terminal :

**gedit ~/.scim/global**

I have typed the above line in as many ways as I can think off It comes back with 

root@s-laptop:/home/s# gedit .scim/global
bash: gedit: command not found
root@s-laptop:/home/s# sudo gedit /.scim/global
sudo: gedit: command not found
root@s-laptop:/home/s#

I assume the ~ means home directory ,, as in # home/s/.scim/global 

any suggestions??  ps .....

when I manually open the file /home/s/.scim/global    with mousepad all that is inside is this line 

/DefaultKeyboardLayout = Japanese


Stephen

---

### Post by basilwatson on 2006-09-06
well I have it typing kanji in mouse pad and Anthy is sitting up there in the tool bar , but I cant get it to type Japanese , here in this reply??

any Ideas ??

Stephen

---

### Post by harerama on 2006-09-06
I am a complete novice so please consider my advice very critically.

When I tried this first time. It seems all messed up and didn"t work. So I removed Japanese language support(system/administration/languagesupport) once then installed again. Then I did the whole process on this page again. ([https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM))
Then im-switch -z en_US -s scim

And it is working beautifully now.

---

### Post by seshomaru samma on 2006-09-07
basilwatson
it seems like you dont have gedit installed for some reason
try 'nano' instead of 'gedit'
are you on Xubuntu?
what text editor do you have?

i think though that harerama's advice is very wise , remove Japanese and start again . Please follow the link in my first post . You only need one command to get SCIM running in Ubuntu (in Xubuntu , if I remember correctly , it works out of the box)

---

### Post by basilwatson on 2006-09-07
Thanks I will try again later , is that remove japanese support in settings , Language support?

I have to get ready to go to work now,  

Thanks for the support, I am nearly there ! 

and all will be working well !

Kind regards 

Stephen

---

