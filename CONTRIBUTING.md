# Contributing

In this document we will dive into the database structure and some guidelines to keep in mind when adding new entries to the database.

# Hop
**Database table containing all Hop info**
| Column        | Description                                                             |
| ------------- | ----------------------------------------------------------------------- |
| Id            | Unique Id                                                               |
| Aroma         | Text description of the aroma                                           |
| BrewingUsage  | FK to LookupBrewingUsage table                                          |
| Name          | Name of the hop                                                         |
| Pedigree      | Text explaining how the hop was cultivated                              |
| AlphaMax      | Maximum amount of alpha acid as a percentage of total weight of the hop |
| AlphaMin      | Minimum amount of alpha acid as a percentage of total weight of the hop |
| BetaMax       | Maximum amount of beta acid as a percentage of total weight of the hop  |
| BetaMin       | Minimum amount of beta acid as a percentage of total weight of the hop  |
| CoHumuloneMax | Maximum amount of cohumulone as a percentage of total alpha acids       |
| CoHumuloneMin | Minimum amount of cohumulone as a percentage of total alpha acids       |
| Info          | Text giving information about the hop                                   |
| Styles        | Text description of suitable styles to use this hop                     |
| TotalOilMax   | Maximum amount of oil in ml/100g                                        |
| TotalOilMin   | Minimum amount of oil in ml/100g                                        |
| TradeInfo     | Text description on how to use the hop and 'trade secrets'              |

### Notes
> If a hop is available from multiple countries, seperate entries must be created and the hop name should be suffixed with `' (<countryCcode>)'`. Hops with a single variety should not have a country code suffix.

## Substitution
**Database table linking hops to each other as substitutes**
| Column | Description                                            |
| ------ | ------------------------------------------------------ |
| HopId  | FK to the Hops table Id of the parent hop              |
| SubId  | FL to the Hops table Id of the possible substitute hop |

## Alias
**Database table adding aliases to a hop name**
| Column | Description             |
| ------ | ----------------------- |
| HopId  | FK to the Hops table Id |
| Name   | Alias name for the Hop  |

## Aroma
**Database table linking aromas to a hop**
| Column  | Description                 |
| ------- | --------------------------- |
| HopId   | FK to the Hops table Id     |
| Profile | FK to the LookupAroma table |

## LookupAroma
**Database table containing all aroma info**
| Column | Description                         |
| ------ | ----------------------------------- |
| Id     | Unique Id                           |
| Name   | Short text description of the aroma |

## LookupBrewingUsage
**Database table containing all brewing usage info**
| Column | Description                                 |
| ------ | ------------------------------------------- |
| Id     | Unique Id                                   |
| Name   | Short text description of the brewing usage |

# Malt
**Database table containing all Malt info**
| Column        | Description                                         |
| ------------- | --------------------------------------------------- |
| Id            | Unique Id                                           |
| Name          | Name of the malt                                    |
| Description   | Text description of the malt                        |
| EBCMin        | Minimum EBC value                                   |
| EBCMax        | Maximum EBC value                                   |
| Maltser       | FK to the LookupMaltser table                       | 
| Ratio         | Maximum percentage of the grist                     |
| Yield         | Maximum percentage of the weight as soluble extract |
| Grain         | FK to LookupGrainType table id                      |
| Moisture      | Maximum moisture content                            |
| DiastaticPower| Grain’s enzymatic content in Windisch-Kolbach units |
| TotalNitrogen | Measure of total nitrogen content of the grain      |
| KolbachIndex  | Relation of soluble protein to total nitrogen       |

### Notes
> If a malt is available from multiple maltsters under the same malt name, seperate entries should be created

## LookupMaltser
**Database table containing all maltser info**
| Column | Description         |
| ------ | ------------------- |
| Id     | Unique Id           |
| Name   | Name of the maltser |

# Yeast
**Database table containing all Yeast info**
| Column          | Description                                |
| --------------- | ------------------------------------------ |
| Id              | Unique Id                                  |
| Name            | Name of the yeast                          |
| Description     | Text description of the yeast              |
| TempMin         | Minimum temperature the yeast will ferment |
| TempMax         | Maximum temperature the yeast will ferment |
| Lab             |                                            |
| AttenuationMin  | Minimum percentage of attenuation          |
| AttenuationMax  | Maximum percentage of attenuation          |
| Form            | FK to LookupYeastForm table Id             |
| Flocculation    | FK to LookupYeastFlocculation table Id     |
| Styles          | Text description of suitable styles        |
| Strain          | FK to LookupYeastStrain table Id           |
| AlcoholTolerance| Maximum ethanol tolerance in fermentation  |

## LookupLab
**Database table containing all lab info**
| Column | Description     |
| ------ | --------------- |
| Id     | Unique Id       |
| Name   | Name of the lab |

## LookupYeastForm
**Database table containing all yeast form info**
| Column | Description            |
| ------ | ---------------------- |
| Id     | Unique Id              |
| Name   | Name of the yeast form |

## LookupYeastFlocculation
**Database table containing all yeast flocculation info**
| Column | Description                          |
| ------ | ------------------------------------ |
| Id     | Unique Id                            |
| Name   | Name of the yeast flocculation level |

## LookupYeastStrain
**Database table containing all yeast strain info**
| Column | Description                 |
| ------ | --------------------------- |
| Id     | Unique Id                   |
| Name   | Name of the strain of yeast |
