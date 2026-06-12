---
title: "Brillo en notebook en ubuntu"
date: 2007-09-07
forum: Argentina Team
---

### Post by niko_3100 on 2007-09-07
Gente alguien sabe donde esta la configuracion del brillo en ubuntu? que archivo es? proque en mi notebook con la tecla para subir y bajar el brillo no tengo brillos intermedios o es todo claro o todo oscuro y para configurarlo tengo que entrar a windows xp y la verdad ya tengo ganas de desintalarlo pero por este pequeñito problema no lo hago. O sea cuand apreto FN brillo + o brillo - hace cualquier cosa, quiero que suba y baje el  brillo normal como lo hace en xp, o en el grub tambien me sube y baja el brillo joya.

---

### Post by FlyerDie on 2007-09-07
probaste desde applications=> settings manager=> desktop ?

El archivo que controla es este:

```
/proc/acpi/video/VID/LCD/brightness
```

Sino chequeate este script que podria ser la otra opcion:

```
#!/usr/bin/perl -w
#===============================================================================
#   adjustBrightness.pl
#===============================================================================
my $file = "/proc/acpi/video/VID/LCD/brightness";

unless (scalar(@ARGV) == 1 and ($ARGV[0] eq "up" or $ARGV[0] eq "down"))
{
  die("You must specify 'up' or 'down'.\n");
}
my $direction = shift();

my $setting = "";
my @levels = ();
open(B, $file) or die("Error opening '$file': $!\n");
while (<B>)
{
  if (m#^current: (\d+)$#)
  {
    $setting = $1;
  }
}
close(B);
chomp($setting);

if ($direction eq "up")
{
  $setting+=12;
}
elsif ($direction eq "down")
{
  $setting-=12;
}
exit(0) if ($setting < 12 or $setting > 84);
open(B, ">$file") or die("Error opening '$file': $!\n");
print(B "$setting\n");
close(B);
```

Seteando (Win+Up & Win+Down) deberia funcionarte 

:guitar:

---

### Post by niko_3100 on 2007-09-07
UF me re perdi mal  mira tengo en /proc/acpi/video/VGA/LCD/ brightness

levels: 100 60 20 28 36 44 52 60 68 76 84 92 100
current: 0

:S

---

### Post by FlyerDie on 2007-09-07
asi lo tengo yo:
```
levels:  7 3 0 1 2 3 4 5 6 7
current: 0
```


fijate aca que comentan lo que te puse mas arriba, al menos fue la solucion que le encontro el flaco:

[http://ubuntuforums.org/showthread.php?t=331514](http://ubuntuforums.org/showthread.php?t=331514)

---

### Post by zspikes on 2007-09-08
proba con esto. Andate a algun tty donde haya una consola ( ctrl+alt+F1 ), y apreta Fn+ la tecla para subir o bajar el brillo. Despues volves al entorno grafico con ctrl+alt+F7
saludos!

---

### Post by Martinius on 2007-09-09
En Añadir y quitar aplicaciones hay un programa que te puede servir, se llama Monitor Settings y permite editar el brillo y el contraste del monitor.

---

### Post by niko_3100 on 2007-09-09
Ese progrmiata que me dijiste no me sirvio. :(

---

