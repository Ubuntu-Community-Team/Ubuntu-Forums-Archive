---
title: "Elmo"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by picnic on 2006-09-13
I want to try and set up elmo so I've installed it. However I have absolutely no idea how to set it up to retrieve my mail or do anything.

Any help would be appreciated.

---

### Post by Najand on 2006-09-13
You can configure almost everything by modifying your
~/.elmorc file.

You have to set variables and functions there. There is a sample .elmorc file comes with it when setting it up. You can copy it to your home directory, and change the variables there. It is a gzipped file in "/usr/share/doc/elmo/examples". So,, you can do something like this:
```

cd /usr/share/doc/elmo/examples/
sudo gunzip sample.elmorc.gz
sudo cp sample.elmorc ~/.elmorc

```
And then edit ".elmorc" using nano, vim or gedit
You can find detailed guidence inside the sample file. use it as a reference.

---

### Post by rlandis on 2006-10-06
When I installed elmo it set itself up. It asked a few questions and set itself up. I however have one problem with it. When I download the emails from my isp it dosen't delete the messages off the mailserver. I have it set up in the elmorc file hook fetch_get_mail fetch_del_mail which is supposed to fetch the mail and then delete it off the server but it dosen't. Thunderbird mail on the same machine with same isp deletes retrived messages.:-k

---

