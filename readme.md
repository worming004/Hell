# Hell package

sur nuget.org, un package appelé Hell est poussé, 2 versions comportent des signatures différentes.

en version 1.0.2, le package Hell ne contient qu'une seule classe

```
namespace Hell;

public class V2HaveBreakingChange
{
    public int Version1() => 1;
}
```

et en version 2.0.4,

```
namespace Hell;

public class V2HaveBreakingChange
{
public int Version2() => 2;
}

```

## Les dépendances :

Le point d'entrée est le projet Host, il contient des références au projet DepA et DepB en local, via chemin relatif.

DepA et DepB sont des projets qui ont des références vers le package Hell, mais avec des versions différentes.
Dep A référence la version 1.0.2 et DepB référence la version 2.0.4. Chacune de ces dépendances utilise la classe V2HaveBreakingChange. Et nous allons voir bientôt que c'est un problème.

## Run app

Lancez Host avec

```
cd Host
dotnet run
```

vous devriez voir un malheureuse exception.

