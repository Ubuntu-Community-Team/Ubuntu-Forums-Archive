---
title: "Medibuntu Woes"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by TBayCrusher on 2008-01-11
I Feel A Fool, But After A Full Day Of Trying I've Been Unsuccessful In Installing This/These Medibuntu Apps
These Directions Are Plain Enough I Can See, But They're Certainly Not Beginner Friendly
A Search Shows Hundreds Of Other Linux Newbies Cannot Get Past These Directions Either
But Unfortunately Few Answers Are Given Them Other Than A RePosting Of The Medibuntu Link
The Main Problem Is I'm Not Sure What To Save For My Specific System & Where To Save It
Note: I'm Using 6.06 With An Intel PIII
*Also, For The Few Text Based Files I've Managed To Save From The Site To A Folder...
There Was No "Ubuntu Package Menu" When I Right Clicked
I'm Frustrated, But Trying To Stay Positive

---

### Post by Perpetual on 2008-01-11
Add medibuntu to your sources list (open a terminal and copy and paste).

For Ubuntu 6.06

```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```

then add the GPG key

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then from within Synaptic, search for the package you want and install.  Synaptic will handle the rest.  Or from the command line, use aptitude or apt-get to install the package

```
sudo aptitude install package
```

or

```
sudo apt-get install package
```

If I am misunderstanding please respond back.

---

### Post by stchman on 2008-01-11
> **TBayCrusher said:**
> I Feel A Fool, But After A Full Day Of Trying I've Been Unsuccessful In Installing This/These Medibuntu Apps
These Directions Are Plain Enough I Can See, But They're Certainly Not Beginner Friendly
A Search Shows Hundreds Of Other Linux Newbies Cannot Get Past These Directions Either
But Unfortunately Few Answers Are Given Them Other Than A RePosting Of The Medibuntu Link
The Main Problem Is I'm Not Sure What To Save For My Specific System & Where To Save It
Note: I'm Using 6.06 With An Intel PIII
*Also, For The Few Text Based Files I've Managed To Save From The Site To A Folder...
There Was No "Ubuntu Package Menu" When I Right Clicked
I'm Frustrated, But Trying To Stay Positive

Try this to install Medibuntu.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You can stop when you have gotten to the sudo apt-get update part.

---

