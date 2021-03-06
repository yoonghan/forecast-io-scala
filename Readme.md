Forecast IO v2 API wrapper in scala
===================================

I know there are at least two Java wrappers, but this will feel cleaner to anyone working on a Scala project and needs weather data.

This is also completely immutable and thread-safe!

Review API Spec for specifics: https://developer.forecast.io/docs/v2

##Quick Examples:

###Standard US

```scala
val forecastIO = ForecastIO("my api key")

val Success(forecast) = forecastIO.forecast("45.157778", "-93.226944")

forecast.currently.summary //=> "Mostly Cloudy"
```

###International

```scala
val forecastIO = ForecastIO("my api key", "si")
```

###Locations

It's hard to just "know" the location points, so you can grab a location using the google maps API

```scala
val Success(location) = Location.search("salt lake city utah")
val Success(forecast) = forecastIO.forecast(location)

forecast.currently.apparentTemperature //=> "58.89"
```

###Dates

You can also get a forecast from a prior or future date.

```scala
val date = new Date(1265076122 * 1000L) //=> Feb 2, 2010
val Success(forecast) = forecastIO.forecast("45.157778", "-93.226944", date)
```

##To publish

Run

```scala
sbt clean compile publish
```
