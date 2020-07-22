# SkyBeam
Basic astronomy package implemented in Haskell, computes positions for the stars, planets, and satellites in orbit around the Earth according to information populated from EU "Galileo" GPS system.

## Examples

### Computing the position of Venus in the sky

```haskell
import qualified Data.Vector as V
import qualified SkyBeam as SB

..

computeVenus :: FilePath -> IO T.Text
computeVenus pathToData = do
  ts <- getCurrentTime
  planetsRaw <- F.read('eu003.bsp')

  let planets = SKB.convert planetsRaw
      earth   = V.find ( == "earth") planets
	  venus   = V.find ( == "venus") planets

  -- Get position at current time
  let position = SB.observe ts earth venus

```
