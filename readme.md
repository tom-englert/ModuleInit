[![Chat on Gitter](https://img.shields.io/gitter/room/fody/fody.svg)](https://gitter.im/Fody/Fody)
[![NuGet Status](https://img.shields.io/nuget/v/ModuleInit.Fody.svg)](https://www.nuget.org/packages/ModuleInit.Fody/)


## This is an add-in for [Fody](https://github.com/Fody/Home/)

![Icon](https://raw.githubusercontent.com/Fody/ModuleInit/master/package_icon.png)

Adds a module initializer to an assembly.


## Usage

See also [Fody usage](https://github.com/Fody/Home/blob/master/pages/usage.md).


### NuGet installation

Install the [ModuleInit.Fody NuGet package](https://nuget.org/packages/ModuleInit.Fody/) and update the [Fody NuGet package](https://nuget.org/packages/Fody/):

```
PM> Install-Package Fody
PM> Install-Package ModuleInit.Fody
```

The `Install-Package Fody` is required since NuGet always defaults to the oldest, and most buggy, version of any dependency.


### Add to FodyWeavers.xml

Add `<ModuleInit/>` to [FodyWeavers.xml](https://github.com/Fody/Home/blob/master/pages/usage.md#add-fodyweaversxml)

```xml
<Weavers>
  <ModuleInit/>
</Weavers>
```


## What it does

Based on Einar Egilsson's suggestion using cecil to create module initializers [http://tech.einaregilsson.com/2009/12/16/module-initializers-in-csharp/]


### Finds a class, in the target assembly, named 'ModuleInitializer' with the following form.

```
public static class ModuleInitializer
{
    public static void Initialize()
    {
        //Init code
    }
}
```


### Injects the following code into the module initializer of the target assembly. This code will be called when the assembly is loaded into memory

```
static <Module>()
{
    ModuleInitializer.Initialize();
}
```


## Icon

Icon courtesy of [The Noun Project](https://thenounproject.com)
