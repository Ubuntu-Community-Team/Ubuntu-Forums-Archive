---
title: "Problemas amb Gnome-do"
date: 2009-02-10
forum: Catalan Team
---

### Post by tanreb20 on 2009-02-10
Hola desde aaquest mati no aconsegueixo fer anar el gnome-do

Quan li dono l'ordre no s'obre i desde consola em diu el seguent:

** (/usr/lib/gnome-do/Do.exe:11142): WARNING **: The following assembly referenced from /usr/lib/gnome-do/Do.exe could not be loaded:
     Assembly:   Mono.Posix    (assemblyref_index=4)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/gnome-do).


```
** (/usr/lib/gnome-do/Do.exe:11142): WARNING **: Could not load file or assembly 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/gnome-do/Do.exe:11142): WARNING **: Missing method Init in assembly /usr/lib/gnome-do/Do.exe, type Mono.Unix.Catalog

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'

```

Alguna idea de que pot ser?

Sembla que no trobi un arxiu, pero jo he eliminat i reinstalar i no u entenc...

---

### Post by directhex on 2009-02-10
> **tanreb20 said:**
> Hola desde aaquest mati no aconsegueixo fer anar el gnome-do

Quan li dono l'ordre no s'obre i desde consola em diu el seguent:

** (/usr/lib/gnome-do/Do.exe:11142): WARNING **: The following assembly referenced from /usr/lib/gnome-do/Do.exe could not be loaded:
     Assembly:   Mono.Posix    (assemblyref_index=4)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/gnome-do).


```
** (/usr/lib/gnome-do/Do.exe:11142): WARNING **: Could not load file or assembly 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/gnome-do/Do.exe:11142): WARNING **: Missing method Init in assembly /usr/lib/gnome-do/Do.exe, type Mono.Unix.Catalog

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'

```

Alguna idea de que pot ser?

Sembla que no trobi un arxiu, pero jo he eliminat i reinstalar i no u entenc...

libmono-posix2.0-cil ?

---

### Post by directhex on 2009-02-10
Wait, make that libmono2.0-cil on Intrepid or earlier

---

### Post by tanreb20 on 2009-02-10
nou error...

després de anar instalant les diferents llibraries que em demanava em salta amb axio:

```

System.IO.FileNotFoundException: Could not load file or assembly 'NDesk.DBus.GLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099' or one of its dependencies.
File name: 'NDesk.DBus.GLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099'
  at Do.Platform.Services.OnServiceChanged (System.Object sender, Mono.Addins.ExtensionNodeEventArgs e) [0x00000] 
  at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged (Mono.Addins.ExtensionNodeEventHandler value) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Fatal 00:34:53.852] [Services] Service of type IPreferencesService not found. Using default service instead.
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 

System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.ExtensionNodeEventArgs.get_ExtensionObject () [0x00000] 
  at Do.Platform.Services.OnServiceChanged (System.Object sender, Mono.Addins.ExtensionNodeEventArgs e) [0x00000] 
  at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged (Mono.Addins.ExtensionNodeEventHandler value) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Error 00:34:53.967] [SystemService] Could not EnsureSingleApplicationInstance: Could not load file or assembly 'NDesk.DBus.GLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099' or one of its dependencies.


```

---

### Post by directhex on 2009-02-11
libndesk-dbus-glib1.0-cil

How did you install Gnome-Do without any of its dependencies?

---

### Post by papapep on 2009-02-11
directhex, many thanks for trying to help, but this is the catalan-speakers subforum, and it is only intended for people being able to write and read in this language. :-)

---

### Post by tanreb20 on 2009-02-11
Crec qeu falla alguna cosa amb el tal **gconf-sharp**...

```


** (Do:8728): WARNING **: The following assembly referenced from /usr/lib/gnome-do/Do.Platform.Linux.dll could not be loaded:
     Assembly:   gconf-sharp    (assemblyref_index=9)
     Version:    2.20.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/gnome-do).


** (Do:8728): WARNING **: Could not load file or assembly 'gconf-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Fatal 16:26:17.560] [Services] Service of type IPreferencesService not found. Using default service instead.
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 

System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.ExtensionNodeEventArgs.get_ExtensionObject () [0x00000] 
  at Do.Platform.Services.OnServiceChanged (System.Object sender, Mono.Addins.ExtensionNodeEventArgs e) [0x00000] 
  at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged (Mono.Addins.ExtensionNodeEventHandler value) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.GConfPreferencesService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 

** (Do:8728): WARNING **: The following assembly referenced from /usr/lib/gnome-do/Do.Interface.Linux.dll could not be loaded:
     Assembly:   gconf-sharp    (assemblyref_index=1)
     Version:    2.20.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/gnome-do).


** (Do:8728): WARNING **: Could not load file or assembly 'gconf-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
  at Do.Core.Controller.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 



```

---

