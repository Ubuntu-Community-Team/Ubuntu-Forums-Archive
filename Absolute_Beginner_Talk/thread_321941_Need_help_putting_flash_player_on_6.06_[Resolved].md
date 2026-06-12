---
title: "Need help putting flash player on 6.06 [Resolved]"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Caesium on 2006-12-19
I've followed instructions I've found and still can't get flashplayer to work.

I've done: sudo apt-get flashplugin-nonfree and a bunch of other stuff I googled and still it does not work.  My system appears to have version 7 on it after I tried installing, but youtube videos still don't work.  I've tried following instructions for upgrading to version 9 but still no go.

I've also tried this method:

wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)

tar xvzf FP9_plugin_beta_112006.tar.gz

sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/

---

### Post by jvc26 on 2006-12-19
Have you enabled the repositories to download the flash plugins from?:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
If so your instructions probably should have worked via the sudo command but if you havent I'd probs try:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_2_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_2_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
... Oh the other thing is: are you running 64bit Ubuntu? as if so it does have issues with flashplayer.
In which case I'd recommend having a look round the forums as I'm sure that issue has been explained several times.
Hope that helps,
Il

---

### Post by jvc26 on 2006-12-19
Bother awfully sorry gave you the edgy info presumed you were on 6.10
for 6.06:

Repos:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
Flash things:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

Sorry about that.
Is there any particular reason you're not using edgy out of interest?
Il

---

### Post by Caesium on 2006-12-19
Thanks for the quick replies.  Even though the first one was for edgy, it worked.  I guess I didn't have the repositories updated, I thought I did.  Everything seems fine now.

I'm not using edgy because this is mostly just a web browsing computer that I set up for my mom a while ago, when edgy wasn't out.  Since it's just used for casual stuff I don't really want to go about upgrading.

Thanks for the help!

---

### Post by jvc26 on 2006-12-19
Not at all, glad it worked :)
Il

---

