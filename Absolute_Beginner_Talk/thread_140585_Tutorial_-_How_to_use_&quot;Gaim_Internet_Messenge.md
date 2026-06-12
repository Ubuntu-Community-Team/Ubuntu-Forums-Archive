---
title: "Tutorial - How to use &quot;Gaim Internet Messenger&quot; to connect to Ubuntu's IRC channel"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-06
Hello all !!!

This is a nice Tutorial for ALL the newbies... (like me)


_For Ubuntu 5.10_:


_Tutorial - How to use Ubuntu's Pre-installed "Gaim Internet Messenger" to connect to Ubuntu's IRC channel (for chatting)_:


_Part 1 – How to Setup an IRC channel account_:

1. Launch the Program named "Gaim".
    To do this, from the Menu, select: "Applications\Internet\Gaim Internet 
    Messenger"

2. Three windows should appear on your screen:
     a. A window with a title name "Login",
     b. A window with a title name "Accounts" &
     c. A window with a title name "Add Account"

    Close the above windows "b" & "c" ("Accounts" & "Add Account").

    From the Window named (with title) "Login", click on the button named 
    "Accounts".
    
    Notice that the above 2 windows ("b" & "c"), we closed earlier, just came up 
    again.

    Basically, the window with a title name "Accounts" is a sub-window under the 
    "Login" window.
    And the window with a title name "Add Account" is a sub-window under the 
    "Accounts" window.

    _Note_:
    I explained the above, because I want you to get acquainted with the "Gaim 
    Internet Messenger's" environment.
    I could have asked you to move directly to the window with the title name "Add 
    Account".
    But I want you to learn which window is located under which (window's) 
    button...

3. Move to the window with the title name "Add Account".
    (An alternative way to get to this, is to you move to the window with the title 
    name"Accounts" &  click on the button named "Add" – but you will end up with 2 
    "Add Account" windows).

4. Under the "Protocol" list, select "IRC".

5. Under the "Screen Name", enter the "nickname" you would like to use.

6. Under the "Server", just type the IRC Server "address" you would like to 
    connect to.
    In an Ubuntu PC, the IRC Server "irc.freenode.net" should be already filled in as 
    default.
    If this is the Server you would like to connect to, leave it as is, otherwise type 
    your preferred IRC Server's address.

7. Leave the "Password" input box Blank.

8. Leave the "Alias" input box Blank.

9. Click on the button named "Save" & the window will close.

10. Congratulations, your account is now created & ready to use.


_Part 2 – How to Connect to your IRC channel account_:

IF your window with a title name "Accounts" is NOT open, perform the following:

     a. Launch the Program named "Gaim".
         To do this, from the Menu, select: "Applications\Internet\Gaim Internet 
         Messenger"

     b. One window should appear on your screen - a window with a title name 
         "Login".
         Click on the button named "Accounts", to launch your "Accounts" window.

     c. Follow the steps shown below.


IF your window with a title name "Accounts" is still open:

1. On the window with a title name "Accounts", click inside the check box named
    "Online".

2. A "Signon" window will appear, attempting to connect you to the IRC Server 
    called "irc.freenode.net".

3. When you get connected, three things should happen:

    a. A standard "Gaim" conversation window will open, telling you you are logged 
        in to the Freenode network.

    b. At the same time on your Top Panel, on the right hand side, right beside your 
        System Date, a yellow "i" icon should appear. That is your "Gaim's Internet 
        Messenger" program icon.

    c. A new window will appear with a title name "Buddy List".

    Now, move inside your NEW "Gaim's" conversation window that popped-up.
    Try to type something inside your Instant Message box & when finished, press 
    "Enter".

4. Congratulations, you have connected to your IRC channel account & typed your 
    first message.


Now that you have setup & connected to an IRC channel account, whenever (in the future) you want to Login in the IRC channel, all you have to do is launch the  program "Gaim Internet Messenger" (from the Menu, select: "Applications\Internet\Gaim Internet Messenger") & on the window with a title name "Login" that appears, click on the button named "Sign on".

Alternatively, you could  Login in the IRC channel, from your Top Panel, beside your System Date, IF you right-click on your yellow "i" icon & select "Accounts".
Inside the window with the title name "Accounts", click on the check box named "Online".
A "Signon" window will appear & will connect you to your favorite IRC Server.


_Part 3 – How to Chat inside the IRC channel_:

In this part we want to give you some commands on how to work inside those IRC channels.

When you typed your first message, in the previous steps in Part 2, probably nobody was inside that IRC channel (you were forwarded into), to respond to you...

So you might want to join a different IRC channel.

_Example_:
To join the Ubuntu IRC channel, inside your Instant Message box, type: "/join #ubuntu".
That should get you connected & ready to chat.

_Note_:
Lots of other users should be found there, since this is a very common IRC channel visited by the Ubuntu community.

To get quickly acquainted with IRC chatting, let me now give you some of the most commonly used commands (people type):


1. To see all the IRC Channels (or Room Lists) that exist, type:

	/list

     _Note_:
     Some Servers will kick you out if you attempt to list ALL the channels.

     That is because:
     1. It slows down their Server,
     2. Their Bandwidth costs (& is waisted),
     3. It takes time (& for them time is money),
     4. It is totally useless, because you will NOT read it all anyways...     

     _Example_:
     For every time, you type the "/list" command, the Server has to send to YOUR 
     PC, 500Kb of data. 
     If many users (at the same time), type a "/list" command, the Server's traffic 
     goes up...
     And the Server guys might pay about 20 EUR for every 10GB of Traffic their Site 
     generates.
     So it is better if you use the command "/list -YES".
     I do NOT know why, but that is what I was suggested...


2. To join an IRC Room, type: 

	/join #name_of_room 	( < - Example: /join #ubuntu – that was what we used before...)

     _Note_:
     The IRC channel you finally decide to enter, depends on the IRC channels 
     actually available to you.
     And that is found, by typing the "/list" command (case 1, shown in Part 3 
      above). 
     Typing that command, will launch a new window with a title named "Room List" 
     & 3 columns inside it, named; "Name", "Users" & "Topic".
     
     a. The "Name" column, lists ALL IRC channels (currently) available.
         An Example could include:
         #solve
         #ubuntu				( < - This is where I got the "#name_of_room" to use above)
         #wiki
         ... etc...

      b. The "Users" column, lists how many users are Logged-in in each IRC channel 
          (currently) available.

      c. The "Topic" column, lists what is the subject in Each IRC channel (currently) 
          available.

     So, you might want to enter an IRC channel "Name"with lots of "Users" in it, to 
     talk about a specific "Topic" you are interested.
     The "/list" command will help you decide in which Room you want to get into.


3. To change your "nickname", type:

	/nick new_nickname		( < - Type something & press "Enter" to verity it changed)


4. If you enter an IRC channel (decide that you like it) & want to save it in a 
    "Favorites" IRC list:

    a. Click on the button named "Add" at the bottom of your IRC window.
    b. Under the "Channel" input box, type the channel's name you would like to 
        add-in to your "Favorites" IRC list (e.g. #ubuntu).
    c. When finished, click on the "Add" button.


5. To create your own IRC channel, type:

	/join #your_own_channel_name

    _Note_:
    a. Hopefully, if you pick/invent a good/successful channel name, many people 
        might visit your channel & your channel will become a visitor's first choice... 
    b. You could also invite people to join your IRC channel room. To do this, from 
        the Menu, select "Conversation\Invite" & then inside the "Buddy" box, type 
        the nickname of the person you would like to invite in your IRC channel room 
        & inside the "Message" type any message you would like to send him (e.g. 
        Come & join my Room: "#welcome" – where "welcome" is the Room name 
        you created/invented).


6. To save all your conversations in a Log:

    a. From the Menu, select "Options\Enable Logging" (the option should be checked).
    b. Type something inside your Instant Message box & when finished, press "Enter".
    c. To verify that the Log has been activated:

        1. From the Menu, select "Conversation\View Log".
        2. Double-click on the Month you are interested, then select the Date & on 
            the right hand side, you should be able to see what you just typed. 


7. To send a PRIVATE Instant Message (IM) to another person in the Room:

    a. On the right-hand side of your window, select the person you would like to 
        PRIVATE Instant Message (IM) to.
    b. Right-click on him/her & select "IM".
    c. A new PRIVATE Tab should be created & you can start a PRIVATE chat inside 
       there.

    Alternatively, you could just type inside your Instant Message box, the following:
    
     /msg name_of_other_person Respond_if_you_get_this...
     (or: Type_what_you_want, blah, blah...)


8. To Add a Friend to your Buddy List window:

    a. On the right-hand side of your window, select the person you would like to 
        Add to your Buddy List.
    b. Right-click on his name & select "Add".
    c. A new window with title "Add Buddy" should show up & you can edit the 
       appropriate fields as you wish.
    d. When finished, click on the button named "Add".
    e. Your NEW Buddy, should now be added to your Buddy List window.

    _Note_:
    If you can NOT view your Buddy List window, you probably closed it when you 
    got connected to the IRC channel.

    To fix this, look on your Top Panel & try to find on the right-side the yellow "i" icon.

     a. Right-click on it & select "Preferences".
     b. Under the Preferences list, select the "Buddy List" option.
     c.  On the right-side click on the check box named "Raise window on events" (it 
          must be checked).
     d. Then, click on the button named "Close".
     
    Now, try to "Add" anybody to your  Buddy List window & when you do it, the 
    Buddy List window should show up.


_Notes_:

1. To find what other list of commands you can type, you can visit the following link:

	http://wiki.jijbent.nl/index.php/Help:IRC_commando's

   Unfortunately the above link is written in the German Language & I do NOT know 
   if there is an English equivalent one...

2. For more information, visit:

	[http://freenode.net/](http://freenode.net/)


Have Fun !!!


P.S.> I would appreciate if somebody has something to Add that corrects me if I 
	 have performed a mistake.

	 PLEASE do it however inside the Ubuntu's "Customization Tips & Tricks" 
         Page, as I have also Posted inside there.

	 Unfortunately when I post there, there is always a lot of DELAY in my posts (I 
         have estimated that it takes 24 hours for a post to actually get posted in 
         there) & I am left wondering whether the Post went right through or got 
         dumped in the proccess...

	 So I always try to post a Tutorial here too !!! (just to be on the safe side).

	 At the same time inside the Ubuntu's "Customization Tips & Tricks" Page, 
         PLEASE do NOT add comments like "thanks dude", or "that's how you do it" 
         because people that want to read a Tutorial, end up reading comments of NO 
         Learning value.

	 Here though, write as many comments as you like !!!

	 Thanks !!!

---

### Post by H.E. Pennypacker on 2006-07-02
Thanks for the guide.  It's been useful.

---

### Post by MaximB on 2006-07-02
what about ubuntu 6.06 ??? some guild....

---

### Post by n00b@linux on 2006-07-02
Thanks for the guide dvarsam.  I've just lost my IRC virginity!

---

### Post by H.E. Pennypacker on 2006-07-02
[QUOTE=MAXDDARK]what about ubuntu 6.06 ??? some guild....[/QUOTE]

It works the same on 6.06 (some things may be slightly different - any difference is due to changes in GAIM).  Whatever the case, it wouldn't be so difficult to show some appreciation, whether you benefited from the guide or not.

---

### Post by McMarley on 2006-07-30
I like your newbie initiation page
but you asked that if anybody sees any
porblems with the info that he tell you,
well the page with the comands that you
suggest is not in GERMAN but ni DUTCH:!: 

happy coffee to all:!: :!: :!:

---

