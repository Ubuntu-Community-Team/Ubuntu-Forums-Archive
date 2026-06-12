---
title: "Amarok and Conky"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by ahoman66 on 2007-06-22
I would like to add amarok to conky but don't know where to put the amarok script file. Does Amarok use MySQL as default? Otherwise Amarok will not work. 

Thanks in advance
Allen

---

### Post by tippit78 on 2007-06-24
No, but Amarok can use MySQL. Run the first time wizard, and it'll give you instructions on how to set it up.

---

### Post by aeiah on 2007-06-24
if you go to the conky website and look at the screenshots, there is one that uses amarok, and the script is linked there. i assume you've already seen this though.

the only feature that needs amarok to be using mysql is the collection statistics. the 'now playing' and progress functions will work regardless of your database choice.

you can store the script wherever you want but the standard place is in .conky in your home folder. you'll see from the example conkyrc script that conky uses this to communicate with the amarok script, which in turn communicates with amarok:

```
$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif

```

just put that in your conkyrc file with your amarok script saved at ~/.conky/amarok, and then set about deleting the features you aren't bothered about seeing (and the features that wont work due to not having mysql set up)

---

### Post by gavin72 on 2007-08-08
Anyone know how to modify the amarok script to give the following info :

No. of Albums by current artist
No. of songs by current artist
Playcount of current song
Rating of current song

Thanks

---

### Post by larryni on 2007-08-09
> **gavin72 said:**
> Anyone know how to modify the amarok script to give the following info :

No. of Albums by current artist
No. of songs by current artist
Playcount of current song
Rating of current song

Thanks
I don't know about the first two, you need to query amarok's database for them. Have a look through the Collection Stats section in the amarok script on the conky website to get an idea how: [http://conky.sourceforge.net/amarok-ke49](http://conky.sourceforge.net/amarok-ke49)

For playcount and ratings add the following 2 lines in the Now Playing Info section of the amarok script:
```

score)
    score=`dcop amarok player score`
    INT=${score/.*}
    echo $INT
    ;;
playCount) dcop amarok player trackPlayCounter ;;
```
Not sure if turning score into an integer that way is the best way of doing it, but it worked ;)

I also modified playCount to display 'never played', 'played once', 'played twice' or 'played n times':
```

playCount)
    count=`dcop amarok player trackPlayCounter`
    if [ $count -eq 0 ]; then
        echo "never played";
    elif [ $count -eq 1 ]; then
        echo "played once";
    elif [ $count -eq 2 ]; then
        echo "played twice";
    else 
        echo "played $count times"
    fi
    ;;
```

Open your .conkyrc and add the following wherever you want the playcount and ratings to appear:
```

${execi 10 /path/to/script/amarok playCount}
${execi 10 /path/to/script/amarok score}
```
The amarok wiki has a list of all the available dcop functions [http://amarok.kde.org/wiki/DCOP_Functions](http://amarok.kde.org/wiki/DCOP_Functions)

Hope this helps.

---

### Post by gavin72 on 2007-08-10
Thanks very much. Greatly appreciated :)

---

### Post by andybleaden on 2008-04-02
Just a very quick question regarding the amarok and conky scripts

Do I need to enter the amarok script in the conky rc script or a seperate bin bash thingy?

---

### Post by larryni on 2008-04-02
> **andybleaden said:**
> Just a very quick question regarding the amarok and conky scripts

Do I need to enter the amarok script in the conky rc script or a seperate bin bash thingy?

The amarok script is a separate bash script. I saved mine in ~/bin. Then call it from .conkyrc with something like
```
${execi 10 /path/to/script/amarok score}
```

---

### Post by minutero on 2008-04-06
Hi i was reading this thread and did everything it says but still conky doesn't show anything from amarok. I'm an absulutely begginer in xubuntu (i guess it will also work in it as in ubuntu) and please i need a very complete guide in how to create de folder and the script for amarok, cause i already add the code in .conkyrc, i copy it from here and paste it in the end of the conkyrc file. Please i need help.

---

### Post by LeWench on 2008-04-11
I am getting this while conky is active:

sh: /home/lewench/scripts/Amarok.sh: Permission denied

Can anyone help me out with this?

---

### Post by darkknight209 on 2008-04-29
> **LeWench said:**
> I am getting this while conky is active:

sh: /home/lewench/scripts/Amarok.sh: Permission denied

Can anyone help me out with this?


You need to set the premissons properly... 
type this in terminal

```
cd /home/lewench/scripts/
chmod 755 Amarok.sh
```

---

### Post by BEaSTFX on 2008-07-19
Can anyone give me the amarok.sh code?

---

